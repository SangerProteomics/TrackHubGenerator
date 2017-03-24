# TrackHubGenerator

## Overview
Through advances in instrumentation proteomic analysis generate huge amounts of data for a single sample. In a proteogenomic setting all sequenced peptides then need to be mapped to their respective genomic coordinates to be visualised in a genome browser. With the demands of high throughput and ever growing datasets genome browsers struggle to readily visualise files of this size containing this type of information. Track hubs are one solution to this problem by providing the data in a binary format through servers. Here we provide a perl-script to generate track hubs from the output of PoGo, a toll which maps peptides and post-translational modifications to their respective genomic coordinates.

## Download and Instiallation
<ol><li>Download the bedTobigBed program as binary from the utilities directory from UCSC (http://hgdownload.soe.ucsc.edu/admin/exe/)</li><li>Download the fetchChromSizes script from the utilities directory from UCSC (http://hgdownload.soe.ucsc.edu/admin/exe/) and store it in the same folder as the bedTobigBed binary file</li><li>Download the TrackHubGenerator from github</li></ol>
You will need to have perl 5.16.2 or higher installed to run this script. Perl can be downloaded here (https://www.perl.org/).

## Learn and Support
The script will generate a folder with subfolders and files as required for a track hub. After successful exit of the script the resulting folder may be moved to an openly accessible server (ftp and http enabled) to be able to load the hub in online genome browsers such as the UCSC Genome Browser, the Ensembl Genome Browser and BioDalliance. For more information about track hubs and how to customize the generated hub further please refer to the UCSC TrackHub Infopage (https://genome.ucsc.edu/goldenpath/help/hgTrackHubHelp.html).

To run the TrackHubGenerator enter the following into a unix shell:

<pre>perl TrackHubGenerator.pl PATH/TO/NAME ASSEMBLY FBED UCSC EMAIL</pre>

Positional arguments:

<table border="0" widht="100%"><tbody><tr><td width="20%">
<pre>PATH/TO/NAME</pre>
</td><td>Path to location where track hub will be created ending with the name for the track hub</td></tr><tr><td>
<pre>ASSEMBLY</pre>
</td><td width="80%">Assembly of the genome for which the track hub shall be used, e.g. hg38</td></tr><tr><td>
<pre>FBED</pre>
</td><td>Path to the folder containing all BED files which should be included in the track hub. Each BED file will result in a separate track</td></tr><tr><td>
<pre>UCSC</pre>
</td><td>Path to the folder containing the bedTobigBed binary and the fetchChromSizes script previously downloaded from UCSC (http://hgdownload.soe.ucsc.edu/admin/exe/)</td></tr><tr><td>
<pre>EMAIL</pre>
</td><td>Email address to be used as contact for people using the track hub</td></tr></tbody></table>

### Step by step
<ol><li>Download the bedTobigBed program binary and the fetchChromSizes script from UCSC (http://hgdownload.soe.ucsc.edu/admin/exe/) and store in a directory - hereafter refered to as ${UCSC}</li>
<li>Navigate to the TrackHubGenerator directory and into the folder matching your operating system.<newline>
<pre>cd ${TRACKHUBGENERATOR_DIR}</pre>
</li><li>Execute the following command to generate a track hub for your PoGo result BED files stored in ${BED_DIR}<newline>
<pre>perl ./TrackHubGenerator.pl ${BED_DIR}/${NAME} hg38 ${BED_DIR} ${UCSC} ${random.email@test.mail}</pre>
<newline>The TrackHubGenerator will create a folder with the specified name ${NAME} in your folder containing the BED files ${BED_DIR} with all files required for a functional track hub.
</li><li>Move this folder to your publicly accessible webserver ${SERVER} via the mv command.
<pre>mv ${BED_DIR}/${NAME} ${FTP}</pre>
</li><li>To load the track hub into a genome browser please go to https://genome.ucsc.edu and navigate to ‘My Data’ -> ‘Track Hubs’. Add the following URL into the URL field and ‘Add Hub’.<newline>http://${SERVER}/${NAME}/hub.txt</li><li>You will be redirected to the main Genome Browser Gateway. Start surfing the track hub on the reference genome through clicking the ‘GO’ button.</li></ol>

### Test Examples
Test examples, requirement specifications and time estimations are available here: ftp://ftp.sanger.ac.uk/pub/teams/17/software/TrackHubGenerator/TrackHubGenerator_Testprocedures.zip.

## Contact
Christoph Schlaffner (christoph.schlaffner@sanger.ac.uk)