-----------------------------------

### Planning for pyramid interactive browsable tables.

Turning back to jQuery, again, if this time I could make it work..

https://forum.jquery.com/topic/run-jquery-code-without-a-web-server

--------------------------------

How to run jquery on local machine
https://www.codecademy.com/en/forum_questions/51205802e1738f7cce000002

From above page

### How to run jquery on local machine

So i figured this out. 
You have to tell the webpage that you want to use jQuery and where it should get it. 
You can either put the latest jQuery file in on your server or link to it. 

**Here is how i did it:**

```html
<script type="text/javascript" src="jquery-1.9.1.min.js"></script>
<script type="text/javascript" src="script.js"></script>
```
I simply downloaded jQuery from http://jquery.com/download/ 
Simply edit this so your path to the file is correct, and it should work :) Mine did!

It also works directly from the web by putting the link, like so:

```html
<script type="text/javascript" src="http://code.jquery.com/jquery-1.9.1.min.js"></script>
<script type="text/javascript" src="script.js"></script>
```

Hope it helps.

----------------------------------

OK, now. 

let's see what can I test this with.

-----------------------------------

```html
  <script type="text/javascript" src="http://code.jquery.com/jquery-1.9.1.min.js"></script>
  <script type="text/javascript" src="script.js"></script>

```

------------------------------------

https://www.sitepoint.com/12-amazing-jquery-tables/

-------------------------------------

https://cdn.datatables.net/1.10.16/js/jquery.dataTables.min.js
https://cdn.datatables.net/1.10.16/css/jquery.dataTables.min.css

--------------------------------------

OK, so how do I include these ?

view-source: https://datatables.net/

--------------------------------------------

```html

<div class="cdn">
    <span>CSS</span>
    <input type="text" value="//cdn.datatables.net/1.10.16/css/jquery.dataTables.min.css" readonly>
</div>

<div class="cdn">
    <span>JS</span>
    <input type="text" value="//cdn.datatables.net/1.10.16/js/jquery.dataTables.min.js" readonly>
</div>

<p>An example of DataTables in action is shown below.</p></div></div>

<p><table id="example" class="display" cellspacing="0" width="100%"><thead><tr><th>Name</th><th>Position</th><th>Office</th><th>Age</th><th>Start date</th><th>Salary</th></tr></thead><tfoot><tr><th>Name</th><th>Position</th><th>Office</th><th>Age</th><th>Start date</th><th>Salary</th></tr></tfoot><tbody><tr><td>Tiger Nixon</td><td>System Architect</td><td>Edinburgh</td><td>61</td><td>2011/04/25</td><td>$320,800</td></tr><tr><td>Garrett Winters</td><td>Accountant</td><td>Tokyo</td><td>63</td><td>2011/07/25</td><td>$170,750</td></tr><tr></tbody></table></p>


```

<p>An example of DataTables in action is shown below.</p></div></div>

<p><table id="example" class="display" cellspacing="0" width="100%"><thead><tr><th>Name</th><th>Position</th><th>Office</th><th>Age</th><th>Start date</th><th>Salary</th></tr></thead><tfoot><tr><th>Name</th><th>Position</th><th>Office</th><th>Age</th><th>Start date</th><th>Salary</th></tr></tfoot><tbody><tr><td>Tiger Nixon</td><td>System Architect</td><td>Edinburgh</td><td>61</td><td>2011/04/25</td><td>$320,800</td></tr><tr><td>Garrett Winters</td><td>Accountant</td><td>Tokyo</td><td>63</td><td>2011/07/25</td><td>$170,750</td></tr><tr></tbody></table></p>

------------------------------------------

So, this should do it :

-------------------------------------------

```html

<HTML>
<head>

<meta http-equiv="expires"
content=0
/>

<div class="cdn">
    <span>CSS</span>
    <input type="text" value="//cdn.datatables.net/1.10.16/css/jquery.dataTables.min.css" readonly>
</div>

<div class="cdn">
    <span>JS</span>
    <input type="text" value="//cdn.datatables.net/1.10.16/js/jquery.dataTables.min.js" readonly>
</div>

</head>


<body>

<p>An example of DataTables in action is shown below.</p></div></div>

<p><table id="example" class="display" cellspacing="0" width="100%"><thead><tr><th>Name</th><th>Position</th><th>Office</th><th>Age</th><th>Start date</th><th>Salary</th></tr></thead><tfoot><tr><th>Name</th><th>Position</th><th>Office</th><th>Age</th><th>Start date</th><th>Salary</th></tr></tfoot><tbody><tr><td>Tiger Nixon</td><td>System Architect</td><td>Edinburgh</td><td>61</td><td>2011/04/25</td><td>$320,800</td></tr><tr><td>Garrett Winters</td><td>Accountant</td><td>Tokyo</td><td>63</td><td>2011/07/25</td><td>$170,750</td></tr><tr></tbody></table></p>


</body>
</HTML>

```

-----------------------------------------------

### Above is firstTry.html 

Shows as a table.
Does not show anything fancy.

Let's fix ..

----------------------------------------------

```html

<div class="cdn">
    <span>CSS</span>
    <input type="text" value="https://cdn.datatables.net/1.10.16/css/jquery.dataTables.min.css" readonly>
</div>

<div class="cdn">
    <span>JS</span>
    <input type="text" value="https://cdn.datatables.net/1.10.16/js/jquery.dataTables.min.js" readonly>
</div>


```

----------------------------------------------

```html

<HTML>
<head>

<meta http-equiv="expires"
content=0
/>


		<script type="text/javascript" language="javascript" src="//cdn.datatables.net/responsive/1.0.0/js/dataTables.responsive.min.js"></script>

		<script type="text/javascript">

		$(document).ready( function () {
			$('#example')
				.addClass( 'nowrap' )
				.dataTable( {
					responsive: true,
					columnDefs: [
						{ targets: [-1, -3], className: 'dt-body-right' }
					]
				} );


		</script>

</head>


<body>

<p>An example of DataTables in action is shown below.</p></div></div>

<p><table id="example" class="display" cellspacing="0" width="100%"><thead><tr><th>Name</th><th>Position</th><th>Office</th><th>Age</th><th>Start date</th><th>Salary</th></tr></thead><tfoot><tr><th>Name</th><th>Position</th><th>Office</th><th>Age</th><th>Start date</th><th>Salary</th></tr></tfoot><tbody><tr><td>Tiger Nixon</td><td>System Architect</td><td>Edinburgh</td><td>61</td><td>2011/04/25</td><td>$320,800</td></tr><tr><td>Garrett Winters</td><td>Accountant</td><td>Tokyo</td><td>63</td><td>2011/07/25</td><td>$170,750</td></tr><tr></tbody></table></p>


</body>
</HTML>

```

---------------------------------

Now it's doing something .

However, takes forever to load.

So not good (or wrongly built).

No, it is still static.

```javascript

$(document).ready(function(){
    $('#myTable').DataTable();
});

```

--------------------------------

https://cdn.datatables.net/1.10.16/js/jquery.dataTables.min.js
https://cdn.datatables.net/1.10.16/css/jquery.dataTables.min.css

--------------------------------

Again ..

--------------------------------

```html

<HTML>
<head>

<meta http-equiv="expires"
content=0
/>

<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/1.10.16/css/jquery.dataTables.css">

		<script type="text/javascript" language="javascript" src="https://cdn.datatables.net/1.10.16/js/jquery.dataTables.js"></script>



		<script type="text/javascript">

		$(document).ready( function () {
			$('#example').dataTable( {
					responsive: true,
					columnDefs: [
						{ targets: [-1, -3], className: 'dt-body-right' }
					]
				} )
				} );


		</script>

</head>


<body>

<p>An example of DataTables in action is shown below.</p></div></div>

<p><table id="example" class="display" cellspacing="0" width="100%"><thead><tr><th>Name</th><th>Position</th><th>Office</th><th>Age</th><th>Start date</th><th>Salary</th></tr></thead><tfoot><tr><th>Name</th><th>Position</th><th>Office</th><th>Age</th><th>Start date</th><th>Salary</th></tr></tfoot><tbody><tr><td>Tiger Nixon</td><td>System Architect</td><td>Edinburgh</td><td>61</td><td>2011/04/25</td><td>$320,800</td></tr><tr><td>Garrett Winters</td><td>Accountant</td><td>Tokyo</td><td>63</td><td>2011/07/25</td><td>$170,750</td></tr><tr></tbody></table></p>


</body>
</HTML>

```

-------------------------------------

### Above is the secondTry.html

Now it shows the dropdown to select how many entries.
No sorting, though ..

Also it is dead ugly so it somehow doesn't get the css in I guess.

Let's see ..

------------------------------------

```html
<HTML>
<head>

<meta http-equiv="expires"
content=0
/>


	<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/1.10.16/css/jquery.dataTables.min.css">


	<script type="text/javascript" language="javascript" src="//code.jquery.com/jquery-1.12.4.js">
	</script>
	<script type="text/javascript" language="javascript" src="https://cdn.datatables.net/1.10.16/js/jquery.dataTables.min.js">
	</script>




		<script type="text/javascript">

		$(document).ready( function () {
			$('#example').dataTable()
				} );


		</script>

</head>


<body>

<p>An example of DataTables in action is shown below.</p></div></div>

<p><table id="example" class="display" cellspacing="0" width="100%"><thead><tr><th>Name</th><th>Position</th><th>Office</th><th>Age</th><th>Start date</th><th>Salary</th></tr></thead><tfoot><tr><th>Name</th><th>Position</th><th>Office</th><th>Age</th><th>Start date</th><th>Salary</th></tr></tfoot><tbody><tr><td>Tiger Nixon</td><td>System Architect</td><td>Edinburgh</td><td>61</td><td>2011/04/25</td><td>$320,800</td></tr><tr><td>Garrett Winters</td><td>Accountant</td><td>Tokyo</td><td>63</td><td>2011/07/25</td><td>$170,750</td></tr><tr></tbody></table></p>


</body>
</HTML>

```

--------------------------

This is some sort of advanced example.

Let's backtrack a little ..

--------------------------

https://datatables.net/examples/basic_init/multi_col_sort.html

----------------------------

```javascript

$(document).ready(function() {
    $('#example').DataTable( {
        columnDefs: [ {
            targets: [ 0 ],
            orderData: [ 0, 1 ]
        }, {
            targets: [ 1 ],
            orderData: [ 1, 0 ]
        }, {
            targets: [ 4 ],
            orderData: [ 4, 0 ]
        } ]
    } );
} );

```

------------------------------

Trying that now .

------------------------------

No luck.

This should be it, though ..

https://datatables.net/examples/basic_init/zero_configuration.html

DataTables has most features enabled by default, so all you need to do to use it with your own tables is to call the construction function: 

```javascript

$().DataTable();.

```

Searching, ordering and paging goodness will be immediately added to the table, as shown in this example.

------------------------------

So, all should work.

Oh dude as it doesn't.

------------------------------

https://www.codeproject.com/Tips/844403/jQuery-Datatables-For-Beginners

------------------------------

Oh, now it works .

------------------------------

Here first working :

### The below is thirdTry.html

------------------------------

```html

<HTML>
<head>


<script src="https://code.jquery.com/jquery-1.11.1.min.js"></script>

<script src="https://cdn.datatables.net/1.10.4/js/jquery.dataTables.min.js"></script>
<link rel="stylesheet" href="https://cdn.datatables.net/1.10.4/css/jquery.dataTables.min.css">


<script type="text/javascript">
$(document).ready
(
function() 
{
  $('#myTesting').DataTable();
} 
);
</script>


</head>


<body>


<table id="myTesting" >

        <thead>
            <tr>
                <th>Name</th>
                <th>Position</th>
                <th>Office</th>
                <th>Age</th>
                <th>Start date</th>
                <th>Salary</th>
            </tr>
        </thead>

        <tbody>
            <tr>
                <td>Tiger Nixon</td>
                <td>System Architect</td>
                <td>Edinburgh</td>
                <td>61</td>
                <td>2011/04/25</td>
                <td>$320,800</td>
            </tr>
            <tr>
                <td>Garrett Winters</td>
                <td>Accountant</td>
                <td>Tokyo</td>
                <td>63</td>
                <td>2011/07/25</td>
                <td>$170,750</td>
            </tr>
            <tr>
                <td>Ashton Cox</td>
                <td>Junior Technical Author</td>
                <td>San Francisco</td>
                <td>66</td>
                <td>2009/01/12</td>
                <td>$86,000</td>
            </tr>
        </tbody>

    </table>

</body>
</HTML>

```

-----------------------------------

This is what we want.

Let's see how slow this is via server (not on public)

-------------------------------------

For that we need to download the sources ..

-------------------------------------

```html

<script src="https://code.jquery.com/jquery-1.11.1.min.js"></script>

<script src="https://cdn.datatables.net/1.10.4/js/jquery.dataTables.min.js"></script>
<link rel="stylesheet" href="https://cdn.datatables.net/1.10.4/css/jquery.dataTables.min.css">

```

-------------------------------------

Almost. not quite.

something is not quite right.

-------------------------------------

WOrks !!!

--------------------------------------

However, I think the css doesn't work ?

Or, maybe they set the CSS somewhere in the script ?

--------------------------------------

jQuery and all its stuff is under MIT license :

https://stackoverflow.com/questions/3902754/mit-vs-gpl-license

The MIT license is GPL-compatible. Is the GPL license MIT-compatible? i.e. I can include MIT-licensed code in a GPL-licensed product, but can I include GPL-licensed code in a MIT-licensed product?

The difference with MIT is that even if you actually distribute your proprietary code that is using the MIT licensed code, you do not have to make the code open source. You can distribute it as a closed app where the code is encrypted or is a binary. Including the MIT-licensed code can be encrypted, as long as it carries the MIT license notice.

Oh, jQuery is double license, luckily !

No - it was double license until 2102

https://blog.jquery.com/2012/09/10/jquery-licensing-changes/

One simplification we made was to remove the GNU General Public License (GPL), leaving only the MIT License. Having just one license option makes things easier for the Foundation to manage and eliminates confusion that existed about the Foundation’s previous dual-licensing policy. 

However, this doesn’t affect your ability to use any of the Foundation’s projects. You are still free to take a jQuery Foundation project, make changes, and re-license it under the GPL if your situation makes that desirable. The Free Software Foundation site confirms that the MIT License is a “lax, permissive non-copyleft free software license, compatible with the GNU GPL.”

--------------------------------------

OK, so MIT license is compatible to be added into GPL work.

--------------------------------------

Well any case now.

--------------------------------------

Why is my thingie not showing the way I wanted ????

---------------------------------------

https://datatables.net/examples/styling/display.html

---------------------------------------

Ah, the TABLE needs to have a CLASS,
which then puts the stripes on it etc !

---------------------------------------

Well that's good ..

---------------------------------------

<table id="example" class="display" cellspacing="0" width="100%">

Yes :) :)

---------------------------------------

And here we have it :

---------------------------------------

```

/home/molhaem2/telenius/jQueryTest
[telenius@deva jQueryTest]$ tree
.
|-- jquery-1.11.1.min.js -> ../jQuery/jquery-1.11.1.min.js
|-- jquery-1.12.4.min.js -> ../jQuery/jquery-1.12.4.min.js
|-- jquery-3.2.1.min.js -> ../jQuery/jquery-3.2.1.min.js
|-- jquery.dataTables.min.css -> ../jQuery/jquery.dataTables.min.css
|-- jquery.dataTables.min.js -> ../jQuery/jquery.dataTables.min.js
|-- site-examples.css -> ../jQuery/site-examples.css
`-- test.html

0 directories, 7 files
[telenius@deva jQueryTest]$ 

[telenius@deva jQueryTest]$ cat test.html 

```

```html

<HTML>
<head>


<script src="jquery-3.2.1.min.js"></script>

<script src="jquery.dataTables.min.js"></script>

<link rel="stylesheet" href="jquery.dataTables.min.css">

<style media="screen" type="text/css">

html body {
   
    margin: auto;
    width: 90%;
    padding: 10px;
    border: 3px solid #f0f0f0;
    max-width:900px;

    line-height: 150%;
    font-family: Helvetica;    
    background-color: #ffffff;
}

</style>

<script type="text/javascript">
$(document).ready
(
function() 
{
  $('#myTesting').DataTable();
} 
);
</script>


</head>


<body>


<table id="myTesting" class="display">

        <thead align="left">
            <tr>
                <th>Name</th>
                <th>Position</th>
                <th>Office</th>
                <th>Age</th>
                <th>Start date</th>
                <th>Salary</th>
            </tr>
        </thead>

        <tbody>
            <tr>
                <td>Tiger Nixon</td>
                <td>System Architect</td>
                <td>Edinburgh</td>
                <td>61</td>
                <td>2011/04/25</td>
                <td>$320,800</td>
            </tr>
            <tr>
                <td>Garrett Winters</td>
                <td>Accountant</td>
                <td>Tokyo</td>
                <td>63</td>
                <td>2011/07/25</td>
                <td>$170,750</td>
            </tr>
            <tr>
                <td>Ashton Cox</td>
                <td>Junior Technical Author</td>
                <td>San Francisco</td>
                <td>66</td>
                <td>2009/01/12</td>
                <td>$86,000</td>
            </tr>
        </tbody>

    </table>

</body>
</HTML>

```

```
[telenius@deva jQueryTest]$ 
```

------------------------------------

Now, making the table of all data in pyramid ..

-------------------------------------

```

[telenius@deva jQueryTest]$ find /t1-data/data/hugheslab/PYRAMID/RUNS -name *PIPE_sampleComments.txt       
/t1-data/data/hugheslab/PYRAMID/RUNS/mouse/ChIP/ter119/H3K4me1/C57/Ter119_H3K4me1_MZ_DH_Jun_2012/rep1/mm9_jk_30Aug2016/Comments_Peaks_Footprints/PIPE_sampleComments.txt
/t1-data/data/hugheslab/PYRAMID/RUNS/mouse/ChIP/ter119/H3K4me3/C57/Ter119_H3K4me3_MZ_DH_Jun_2012/rep1/mm9_jk_26Aug2016/Comments_Peaks_Footprints/PIPE_sampleComments.txt
/t1-data/data/hugheslab/PYRAMID/RUNS/mouse/ChIP/ter119/Input/C57/Rad21input_LH_DH_Mar_2013/rep1/mm9_jt_19Oct2016/Comments_Peaks_Footprints/PIPE_sampleComments.txt
/t1-data/data/hugheslab/PYRAMID/RUNS/mouse/ChIP/ter119/Input/C57/Ter119_HistoneInput_MZ_DH_Jun_2012/rep1/mm9_jk_31Aug2016/Comments_Peaks_Footprints/PIPE_sampleComments.txt
/t1-data/data/hugheslab/PYRAMID/RUNS/mouse/ChIP/ter119/RAD21/C57/Rad21Cohesin_LH_DH_Mar_2013/rep2/mm9_jt_19Oct2016/Comments_Peaks_Footprints/PIPE_sampleComments.txt
/t1-data/data/hugheslab/PYRAMID/RUNS/mouse/ChIP/ter119/RAD21/C57/Rad21Cohesin_LH_DH_Mar_2013/rep1/mm9_jt_19Oct2016/Comments_Peaks_Footprints/PIPE_sampleComments.txt
/t1-data/data/hugheslab/PYRAMID/RUNS/mouse/ChIP/ter119_spleen/Ezh2/C57/Ezh2_C57_Ter119_LH_DH_May_2016/rep3/mm9_ch_28Jun2017/Comments_Peaks_Footprints/PIPE_sampleComments.txt
/t1-data/data/hugheslab/PYRAMID/RUNS/mouse/ChIP/ter119_spleen/Ezh2/C57/Ezh2_C57_Ter119_LH_DH_May_2016/rep1/mm9_ch_28Jun2017/Comments_Peaks_Footprints/PIPE_sampleComments.txt
/t1-data/data/hugheslab/PYRAMID/RUNS/mouse/ChIP/ter119_spleen/Ezh2/C57/Ezh2_C57_Ter119_LH_DH_May_2016/rep2/mm9_ch_28Jun2017/Comments_Peaks_Footprints/PIPE_sampleComments.txt


```
--------------------------------------

```

[telenius@deva jQueryTest]$ find /t1-data/data/hugheslab/PYRAMID/RUNS/mouse/ChIP/ter119/H3K4me1/C57/Ter119_H3K4me1_MZ_DH_Jun_2012/rep1/mm9_jk_30Aug2016 -name PIPE_*.txt 
/t1-data/data/hugheslab/PYRAMID/RUNS/mouse/ChIP/ter119/H3K4me1/C57/Ter119_H3K4me1_MZ_DH_Jun_2012/rep1/mm9_jk_30Aug2016/PipeRun/PIPE_hubbingSymbolic.txt
/t1-data/data/hugheslab/PYRAMID/RUNS/mouse/ChIP/ter119/H3K4me1/C57/Ter119_H3K4me1_MZ_DH_Jun_2012/rep1/mm9_jk_30Aug2016/PipeRun/PIPE_metadata.txt
/t1-data/data/hugheslab/PYRAMID/RUNS/mouse/ChIP/ter119/H3K4me1/C57/Ter119_H3K4me1_MZ_DH_Jun_2012/rep1/mm9_jk_30Aug2016/PipeRun/PIPE_ChIP_metadata.txt
/t1-data/data/hugheslab/PYRAMID/RUNS/mouse/ChIP/ter119/H3K4me1/C57/Ter119_H3K4me1_MZ_DH_Jun_2012/rep1/mm9_jk_30Aug2016/PipeRun/PIPE_fastqPaths.txt
/t1-data/data/hugheslab/PYRAMID/RUNS/mouse/ChIP/ter119/H3K4me1/C57/Ter119_H3K4me1_MZ_DH_Jun_2012/rep1/mm9_jk_30Aug2016/Comments_Peaks_Footprints/PIPE_sampleComments.txt
[telenius@deva jQueryTest]$ 

```

---------------------------------------

```

[telenius@deva jQueryTest]$ tree /t1-data1/WTSA/PYRAMID/FASTQ/ChIP/mouse/ter119/H3K4me1/C57/Ter119_H3K4me1_MZ_DH_Jun_2012/rep1
/t1-data1/WTSA/PYRAMID/FASTQ/ChIP/mouse/ter119/H3K4me1/C57/Ter119_H3K4me1_MZ_DH_Jun_2012/rep1 [error opening dir]

```

( as organism and data type were moved vice versa )

```

[telenius@deva jQueryTest]$ tree /t1-data1/WTSA/PYRAMID/FASTQ/mouse/ChIP/ter119/H3K4me1/C57/Ter119_H3K4me1_MZ_DH_Jun_2012/rep1
/t1-data1/WTSA/PYRAMID/FASTQ/mouse/ChIP/ter119/H3K4me1/C57/Ter119_H3K4me1_MZ_DH_Jun_2012/rep1
|-- md5sums
|   |-- mdsums_R1afterCopy.txt
|   |-- mdsums_R1beforeCopy.txt
|   |-- mdsums_R1gzipped.txt
|   |-- mdsums_R1unzipped.txt
|   |-- mdsums_R2afterCopy.txt
|   |-- mdsums_R2beforeCopy.txt
|   |-- mdsums_R2gzipped.txt
|   `-- mdsums_R2unzipped.txt
|-- PIPE_ChIP_metadata.txt
|-- PIPE_fastqPaths.txt
|-- PIPE_metadata.txt
|-- PIPE_sampleComments.txt
|-- PyramidVersion.txt
|-- Ter119_H3K4me1_1.fq.gz
|-- Ter119_H3K4me1_2.fq.gz
`-- WhoStoredThis_and_WhereFastqsCameFrom.txt

1 directory, 16 files
[telenius@deva jQueryTest]$ 

```

WhoStoredThis_and_WhereFastqsCameFrom.txt

-----------------------------------

"Starting small"

```
/t1-data/data/hugheslab/PYRAMID/RUNS/mouse/ChIP/ter119/H3K4me1/C57/Ter119_H3K4me1_MZ_DH_Jun_2012/rep1/mm9_jk_30Aug2016/PipeRun

find /t1-data/data/hugheslab/PYRAMID/RUNS -name *PIPE_metadata.txt > filelist.txt

cat filelist.txt | sed 's/\/PipeRun\/PIPE_metadata.txt//' | sed 's/\//<td>/' | sed 's/$/</td>/'

```

-------------------------------------

```

[telenius@deva jQueryTest]$ echo "tr" | cat filelist.txt - | sed 's/\/PipeRun\/PIPE_metadata.txt//' | sed 's/\/t1-data\/data\/hugheslab\/PYRAMID\/RUNS//' | sed 's/\//\n<td>/g' | sed 's/$/<\/td>/' | sed 's/^<\/td>$/<\/tr><tr>/' | awk '{if(NR==1)print "<tr>"; else {print $0}}' | sed 's/^tr<\/td>/<\/tr>/'

```

--------------------------------------

```

[telenius@deva jQueryTest]$ echo "tr" | cat filelist.txt - | sed 's/\/Comments_Peaks_Footprints\/PIPE_sampleComments.txt$//' | sed 's/\/t1-data\/data\/hugheslab\/PYRAMID\/RUNS//' | sed 's/\//\n<td>/g' | rev | sed 's/_/\//' | sed 's/_/\//' | rev | sed 's/\//\n<td>/g' | sed 's/$/<\/td>/' | sed 's/^<\/td>$/<\/tr><tr>/' | awk '{if(NR==1)print "<tr>"; else {print $0}}' | sed 's/^tr<\/td>/<\/tr>/' > testi.txt

```

---------------------------------------

Easier to make it with paste.

------------------------------------------

```

[telenius@deva jQueryTest]$ cat filelist.txt | sed 's/\//\t/g' | cut -f 9-14
ter119  H3K4me1 C57     Ter119_H3K4me1_MZ_DH_Jun_2012   rep1    mm9_jk_30Aug2016
ter119  H3K4me3 C57     Ter119_H3K4me3_MZ_DH_Jun_2012   rep1    mm9_jk_26Aug2016
ter119  Input   C57     Rad21input_LH_DH_Mar_2013       rep1    mm9_jt_19Oct2016
ter119  Input   C57     Ter119_HistoneInput_MZ_DH_Jun_2012      rep1    mm9_jk_31Aug2016
ter119  RAD21   C57     Rad21Cohesin_LH_DH_Mar_2013     rep2    mm9_jt_19Oct2016
ter119  RAD21   C57     Rad21Cohesin_LH_DH_Mar_2013     rep1    mm9_jt_19Oct2016
ter119_spleen   Ezh2    C57     Ezh2_C57_Ter119_LH_DH_May_2016  rep3    mm9_ch_28Jun2017
ter119_spleen   Ezh2    C57     Ezh2_C57_Ter119_LH_DH_May_2016  rep1    mm9_ch_28Jun2017
ter119_spleen   Ezh2    C57     Ezh2_C57_Ter119_LH_DH_May_2016  rep2    mm9_ch_28Jun2017
[telenius@deva jQueryTest]$ cat filelist.txt | sed 's/\//\t/g' | cut -f 9-14 > cutted.txt

```

------------------------------------------

```
cat filelist.txt | sed 's/\//\t/g' | cut -f 9-11 > cutted911.txt
cat filelist.txt | sed 's/\//\t/g' | cut -f 12 | rev | sed 's/_/\t/' | sed 's/_/\t/' | sed 's/_/\t/'  | sed 's/_/\t/'| rev > cutted12.txt
cat filelist.txt | sed 's/\//\t/g' | cut -f 14 | rev | sed 's/_/\t/' | sed 's/_/\t/' | rev > cutted14.txt
cat filelist.txt | sed 's/\//\t/g' | cut -f 13 > cutted13.txt
paste cutted911.txt cutted12.txt cutted13.txt cutted14.txt > cuttedTabbed.txt

cat cuttedTabbed.txt | sed 's/^/<tr><td>/' | sed 's/\t/<td><\/td>/g' | sed 's/$/<\/td<\/tr>/' > parsed.txt

cat cuttedTabbed.txt | sed 's/^/<tr><td>/' | sed 's/\t/<\/td><td>/g' | sed 's/$/<\/td><\/tr>/' > parsed.txt
cat begin.txt parsed.txt end.txt > test3.html 

```
----------------------

Oh dude it auto-enables multi-column sorting !!!

https://datatables.net/examples/basic_init/multi_col_sort.html

----------------------

That is amazing.

Amazing.

----------------------

Making the full table then !

-----------------------

```

nohup nice find /t1-data/data/hugheslab/PYRAMID/RUNS/mouse/ChIP -name PIPE_sampleComments.txt > mousechipfilelist.txt &
nohup nice find /t1-data/data/hugheslab/PYRAMID/RUNS/mouse/ATAC -name PIPE_sampleComments.txt > mouseaccessibilityfilelist.txt &

nohup nice find /t1-data/data/hugheslab/PYRAMID/RUNS/human/ChIP -name PIPE_sampleComments.txt > humanchipfilelist.txt &
nohup nice find /t1-data/data/hugheslab/PYRAMID/RUNS/human/ATAC -name PIPE_sampleComments.txt > humanaccessibilityfilelist.txt &


nohup nice find /t1-data/data/hugheslab/PYRAMID/RUNS/mouse/DNaseI -name PIPE_sampleComments.txt >> mouseaccessibilityfilelist.txt &
nohup nice find /t1-data/data/hugheslab/PYRAMID/RUNS/human/DNaseI -name PIPE_sampleComments.txt >> humanaccessibilityfilelist.txt &

```

------------------------------------------

```bash

doItForChip(){

cat ${filelist}filelist.txt | sed 's/\//\t/g' | cut -f 9-11 > cutted911.txt
cat ${filelist}filelist.txt | sed 's/\//\t/g' | cut -f 12 | rev | sed 's/_/\t/' | sed 's/_/\t/' | sed 's/_/\t/'  | sed 's/_/\t/'| rev > cutted12.txt
cat ${filelist}filelist.txt | sed 's/\//\t/g' | cut -f 14 | rev | sed 's/_/\t/' | sed 's/_/\t/' | rev > cutted14.txt
cat ${filelist}filelist.txt | sed 's/\//\t/g' | cut -f 13 > cutted13.txt
paste cutted911.txt cutted12.txt cutted13.txt cutted14.txt > cuttedTabbed.txt

cat cuttedTabbed.txt | sed 's/^/<tr><td>/' | sed 's/\t/<\/td><td>/g' | sed 's/$/<\/td><\/tr>/' > parsed.txt
cat chipbegin.txt parsed.txt end.txt > ${filelist}.html 

}


doItForAccessibility(){

cat ${filelist}filelist.txt | sed 's/\//\t/g' | cut -f 8-10 > cutted810.txt
cat ${filelist}filelist.txt | sed 's/\//\t/g' | cut -f 11 | rev | sed 's/_/\t/' | sed 's/_/\t/' | sed 's/_/\t/'  | sed 's/_/\t/'| rev > cutted11.txt
cat ${filelist}filelist.txt | sed 's/\//\t/g' | cut -f 13 | rev | sed 's/_/\t/' | sed 's/_/\t/' | rev > cutted13.txt
cat ${filelist}filelist.txt | sed 's/\//\t/g' | cut -f 12 > cutted12.txt
paste cutted810.txt cutted11.txt cutted12.txt cutted13.txt > cuttedTabbed.txt

cat cuttedTabbed.txt | sed 's/^/<tr><td>/' | sed 's/\t/<\/td><td>/g' | sed 's/$/<\/td><\/tr>/' > parsed.txt
cat accessibilitybegin.txt parsed.txt end.txt > ${filelist}.html 

}

# -----------------------

filelist="mousechip"
doItForChip

filelist="humanchip"
# doItForChip


# -----------------------

filelist="mouseaccessibility"
doItForAccessibility

filelist="humanaccessibility"
# doItForAccessibility

```

----------------------------

That is amazing.

That really is.

----------------------------

Making the full script :

----------------------------

```bash

#!/bin/bash

echo 
echo "Generating PYRAMID html listings .."
echo
echo
hostname
echo
pwd
echo
echo $0
echo
date
echo
module purge
module list
echo


doItForChip(){

cat ${filelist}filelist.txt | sed 's/\//\t/g' | cut -f 9-11 > cutted911.txt
cat ${filelist}filelist.txt | sed 's/\//\t/g' | cut -f 12 | rev | sed 's/_/\t/' | sed 's/_/\t/' | sed 's/_/\t/'  | sed 's/_/\t/'| rev > cutted12.txt
cat ${filelist}filelist.txt | sed 's/\//\t/g' | cut -f 14 | rev | sed 's/_/\t/' | sed 's/_/\t/' | rev > cutted14.txt
cat ${filelist}filelist.txt | sed 's/\//\t/g' | cut -f 13 > cutted13.txt
paste cutted911.txt cutted12.txt cutted13.txt cutted14.txt > cuttedTabbed.txt

cat cuttedTabbed.txt | sed 's/^/<tr><td>/' | sed 's/\t/<\/td><td>/g' | sed 's/$/<\/td><\/tr>/' > parsed.txt
cat chipbegin.txt parsed.txt end.txt > ${filelist}.html 

}


doItForAccessibility(){

cat ${filelist}filelist.txt | sed 's/\//\t/g' | cut -f 8-10 > cutted810.txt
cat ${filelist}filelist.txt | sed 's/\//\t/g' | cut -f 11 | rev | sed 's/_/\t/' | sed 's/_/\t/' | sed 's/_/\t/'  | sed 's/_/\t/'| rev > cutted11.txt
cat ${filelist}filelist.txt | sed 's/\//\t/g' | cut -f 13 | rev | sed 's/_/\t/' | sed 's/_/\t/' | rev > cutted13.txt
cat ${filelist}filelist.txt | sed 's/\//\t/g' | cut -f 12 > cutted12.txt
paste cutted810.txt cutted11.txt cutted12.txt cutted13.txt > cuttedTabbed.txt

cat cuttedTabbed.txt | sed 's/^/<tr><td>/' | sed 's/\t/<\/td><td>/g' | sed 's/$/<\/td><\/tr>/' > parsed.txt
cat accessibilitybegin.txt parsed.txt end.txt > ${filelist}.html 

}

# -----------------------

find /t1-data/data/hugheslab/PYRAMID/RUNS/mouse/ChIP -name PIPE_sampleComments.txt > mousechipfilelist.txt &
find /t1-data/data/hugheslab/PYRAMID/RUNS/mouse/ATAC -name PIPE_sampleComments.txt > mouseaccessibilityfilelist.txt &
find /t1-data/data/hugheslab/PYRAMID/RUNS/mouse/DNaseI -name PIPE_sampleComments.txt >> mouseaccessibilityfilelist.txt &

find /t1-data/data/hugheslab/PYRAMID/RUNS/human/ChIP -name PIPE_sampleComments.txt > humanchipfilelist.txt &
find /t1-data/data/hugheslab/PYRAMID/RUNS/human/ATAC -name PIPE_sampleComments.txt > humanaccessibilityfilelist.txt &
find /t1-data/data/hugheslab/PYRAMID/RUNS/human/DNaseI -name PIPE_sampleComments.txt >> humanaccessibilityfilelist.txt &

# -----------------------

filelist="mousechip"
doItForChip

filelist="humanchip"
# doItForChip


# -----------------------

filelist="mouseaccessibility"
doItForAccessibility

filelist="humanaccessibility"
# doItForAccessibility


echo
date
echo
echo "All done !" 
echo

```

----------------------------

```bash

#!/bin/bash

echo 
echo "Generating PYRAMID html listings .."
echo
echo
hostname
echo
pwd
echo
echo $0
echo
date
echo
module purge
module list
echo


doItForChip(){

cat ${filelist}filelist.txt | sed 's/\//\t/g' | cut -f 9-11 > cutted911.txt
cat ${filelist}filelist.txt | sed 's/\//\t/g' | cut -f 12 | rev | sed 's/_/\t/' | sed 's/_/\t/' | sed 's/_/\t/'  | sed 's/_/\t/'| rev > cutted12.txt
cat ${filelist}filelist.txt | sed 's/\//\t/g' | cut -f 14 | rev | sed 's/_/\t/' | sed 's/_/\t/' | rev > cutted14.txt
cat ${filelist}filelist.txt | sed 's/\//\t/g' | cut -f 13 > cutted13.txt
paste cutted911.txt cutted12.txt cutted13.txt cutted14.txt > cuttedTabbed.txt

cat cuttedTabbed.txt | sed 's/^/<tr><td>/' | sed 's/\t/<\/td><td>/g' | sed 's/$/<\/td><\/tr>/' > parsed.txt
cat chipbegin.txt parsed.txt end.txt > ${filelist}.html 

cp ${filelist}.html ../HTML/.

}


doItForAccessibility(){

cat ${filelist}filelist.txt | sed 's/\//\t/g' | cut -f 8-10 > cutted810.txt
cat ${filelist}filelist.txt | sed 's/\//\t/g' | cut -f 11 | rev | sed 's/_/\t/' | sed 's/_/\t/' | sed 's/_/\t/'  | sed 's/_/\t/'| rev > cutted11.txt
cat ${filelist}filelist.txt | sed 's/\//\t/g' | cut -f 13 | rev | sed 's/_/\t/' | sed 's/_/\t/' | rev > cutted13.txt
cat ${filelist}filelist.txt | sed 's/\//\t/g' | cut -f 12 > cutted12.txt
paste cutted810.txt cutted11.txt cutted12.txt cutted13.txt > cuttedTabbed.txt

cat cuttedTabbed.txt | sed 's/^/<tr><td>/' | sed 's/\t/<\/td><td>/g' | sed 's/$/<\/td><\/tr>/' > parsed.txt
cat accessibilitybegin.txt parsed.txt end.txt > ${filelist}.html 

cp ${filelist}.html ../HTML/.

}

# -----------------------

rm -rf TEMPdir
mkdir TEMPdir
cd TEMPdir

# -----------------------

find /t1-data/data/hugheslab/PYRAMID/RUNS/mouse/ChIP -name PIPE_sampleComments.txt > mousechipfilelist.txt &
find /t1-data/data/hugheslab/PYRAMID/RUNS/mouse/ATAC -name PIPE_sampleComments.txt > mouseaccessibilityfilelist.txt &
find /t1-data/data/hugheslab/PYRAMID/RUNS/mouse/DNaseI -name PIPE_sampleComments.txt >> mouseaccessibilityfilelist.txt &

find /t1-data/data/hugheslab/PYRAMID/RUNS/human/ChIP -name PIPE_sampleComments.txt > humanchipfilelist.txt &
find /t1-data/data/hugheslab/PYRAMID/RUNS/human/ATAC -name PIPE_sampleComments.txt > humanaccessibilityfilelist.txt &
find /t1-data/data/hugheslab/PYRAMID/RUNS/human/DNaseI -name PIPE_sampleComments.txt >> humanaccessibilityfilelist.txt &

# -----------------------

filelist="mousechip"
doItForChip

filelist="humanchip"
# doItForChip


# -----------------------

filelist="mouseaccessibility"
doItForAccessibility

filelist="humanaccessibility"
# doItForAccessibility

# -----------------------

rm -rf TEMPdir


echo
date
echo
echo "All done !" 
echo

```

----------------------------

```
/home/molhaem2/telenius/PYRAMID/Dnase/pyramidLister/updateHtmlTables.sh
```

----------------------------

viewing commands :

```
firefox /home/molhaem2/telenius/PYRAMID/Dnase/pyramidLister/HTML/mouseaccessibility.html
firefox /home/molhaem2/telenius/PYRAMID/Dnase/pyramidLister/HTML/mousechip.html


firefox /home/molhaem2/telenius/PYRAMID/Dnase/pyramidLister/HTML/GEOmouseaccessibility.html
firefox /home/molhaem2/telenius/PYRAMID/Dnase/pyramidLister/HTML/GEOmousechip.html

```

------------------------------

