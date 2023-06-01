# Commands for the simulation of the Melt form of Water
```console
gmx grompp -f em.mdp -o em.tpr -pp em.top -po em.mdp -c melt.gro
```
```console
gmx mdrun -s em.tpr -o em.trr -x em.xtc -c em.gro -e em.edr -g em.log
```
```console
  gmx grompp -f nvt.mdp -o nvt.tpr -pp nvt.top -po nvt.mdp -c em.gro -maxwarn 1
```
```console
 gmx mdrun -s nvt.tpr -o nvt.trr -x nvt.xtc -c nvt.gro -e nvt.edr -g nvt.log
 ```
 ```console
   gmx grompp -f npt.mdp -o npt.tpr -pp npt.top -po npt.mdp -c nvt.gro
 ```
 ```console
 gmx mdrun -s npt.tpr -o npt.trr -x npt.xtc -c npt.gro -e npt.edr -g npt.log
``` 

```console
#Energy minimization
gmx_mpi grompp -f em.mdp -c box.gro -p topol.top -o em.tpr
gmx_mpi mdrun -v -deffnm em -ntomp 39

#nvt -> temprature equiviblrium
gmx_mpi grompp -f nvt.mdp -c em.gro -r em.gro -p topol.top -o nvt.tpr
gmx_mpi mdrun -v -deffnm nvt -ntomp 39

#npt -> pressure equiviblrium
gmx_mpi grompp -f npt.mdp -c nvt.gro -r nvt.gro -t nvt.cpt -p topol.top -o npt.tpr
gmx_mpi mdrun -v -deffnm npt -ntomp 39
```