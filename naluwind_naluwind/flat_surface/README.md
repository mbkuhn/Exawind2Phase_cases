This case serves to recreate an issue in the overset assembly process, likely occuring in Tioga or in the connection between Tioga and Nalu_Wind. The basic issue is that iblank != -1 along all of the patch interface resulting in erroneous overset boundary values in velocity that quickly blow up. To recreate the issue, run 1 time step with a few MPI ranks and look at iblank and the flow velocity along the edges of the interior block. 

Some things to note :
- Recent fixes between Tioga and Nalu_Wind have not fixed this case
- The false iblank values do not occur near processor boundaries.


To run this case :
- modify DropletVOFAuxFunction.C in Nalu_Wind by commenting out the std::erf(radius / ... term so that you run a flat interface
- run naluX as usual using the .yaml file provided. 
