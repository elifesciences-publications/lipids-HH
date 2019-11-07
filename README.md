### This code is associated with the paper from Kinnebrew et al., "Cholesterol accessibility at the ciliary membrane controls hedgehog signaling". eLife, 2019. http://dx.doi.org/10.7554/eLife.50051


1. Download the MATLAB toolbox from the Bio-Formats downloads page. Unzip bfmatlab.zip and add the unzipped bfmatlab folder to your MATLAB path.
2. Create a working directory to store all four MATLAB files (snapShots.m, quant_cilia_mask_for_field.m, get_max_z_projections_github.m, and ciliaMaskFinder_github.m), the bfmatlab folder and your image file (in the Leica image file (.lif) format).
3. Open get_max_z_projections_github.m and set the path to the bfmatlab folder.
4. Open ciliaMaskFinder_github.m and set add the name of your image file.
5. Set your PARAMS in the ciliaMaskFinder_github.m file
        a. Specify the number of channels in your .lif file
	      b. Specify the order/position of each channel in your .lif file  (if the dapi channel is first, give it value of 1,etc.)
	      c. Specify the number of fields in your .lif file and the number of markers to search for
        d. Specify the thresholding that will be applied to the cilia channel (this is user defined and will take some trial and error)
 	      e. Specify how much to dilate the cilia mask in order to create your background mask (lines 54 and 56) 
6.	Run ciliaMaskFinder_github.m code 
7.	Three .csv files will be returned (to your working directory folder) when the code is finished. 
    	  a. The ‘filename_cilia_stats.csv’ file contains the area (row 1) and length (row 2) of each cilia quantified
    	  b. The ‘filename_z_stats.csv’ file contains the information for each cilia separated into focal planes (each row is a different cilia, each column is a focal plane). If n= the number of rows:
	          i. Rows 1 to (n / 3) contain the average pixel intensities within a given cilia mask
	          ii. Rows (n/3 + 1) to n/3 *2 contain the average pixel intensities within the background mask (cilia mask dilated – initial cilia mask = background mask) 
	          iii. Rows (n/3 *2 + 1) to n contain the average pixel intensities within the cilia channel (use this to find which focal planes contain the actual cilia signal) 
