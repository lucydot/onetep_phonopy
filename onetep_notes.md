
### onetep notes, from periodic DFT codes workshop - Daresbury 01/19

- kernel_cutoff can be adjusted to move into the linear scaling regime but even without this there are efficiency gains as using localised basis set and sparse matrices.

- density kernal is printed as a binary file but there are tools to print out density as a cube file

- NGWF radius: 8/9 or even 10 bohr for very high accuracy. 6/7 for quick and dirty. 

- NGWF number:1 - s, 4 - p, 6 - d, but need to consider semicore electrons (look at output where it tells you the number of electrons considered)

- c2x to convert between different file formats

- phonon calculations:
    - The force constants are written in raw format but Joseph wrote a script to convert to txt
	- To compile the force_const_read.f90 on Archer:
		- "module swap PrgEnv-cray PrgEnv-intel","ftn -o force_const_read force_const_read.f90"
	- To use it use eg: "for i in {1..18} ; do echo -e "$i\n6\n" | ./force_const_read > force_constant_$i.dat; done" where 6 is the number of atoms in the supercell for this example
    - .force_consts_1 contains atom_1 displaced in x, .force_consts_2 contains atom_1 displaced in y and so on...
	    - Each file contains a 3xN array (atom 1_x,atom2_x,atom3_x, atom4_x...atomN_x,atomN_y,atomN_z)












