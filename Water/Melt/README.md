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