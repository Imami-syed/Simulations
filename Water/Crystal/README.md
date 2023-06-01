```code 
gmx pdb2gmx -f crystal.pdb -o crystal.gro -p topol.top
```
```console
inputs : 15 2 
input files : crystal.pdb 
generated files : crystal.gro topol.top 
```
```code 
gmx editconf -f crystal.gro -o crystal.gro -c -box 10 10 10
```
```code 
gmx grompp -f em.mdp -o em.tpr -pp em.top -po em.mdp -c crystal.gro
```
```code 
gmx mdrun -s em.tpr -o em.trr -x em.xtc -c em.gro -e em.edr -g em.log
```
```code
gmx grompp -f nvt.mdp -o nvt.tpr -pp nvt.top -po nvt.mdp -c em.gro
```
```code
gmx mdrun -s nvt.tpr -o nvt.trr -x nvt.xtc -c nvt.gro -e nvt.edr -g nvt.log
```
```code 
gmx grompp -f npt.mdp -o npt.tpr -pp npt.top -po npt.mdp -c nvt.gro
```
```code 
gmx mdrun -s npt.tpr -o npt.trr -x npt.xtc -c npt.gro -e npt.edr -g npt.log
```
```console 
vmd crystal.gro npt.xtc 
can be used to check the simulations
```