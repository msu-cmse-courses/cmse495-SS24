[Link to this jupyter notebook](./Files/0204-Web_Scraping.ipynb)

# In-Class Assignment: Web Scraping

Today we will be exploring some of the extensive datasets available at the National Oceanic and Atmospheric Administration (NOAA). Work as a team to try to get as many of todays activities done.  We will meet as a class again around 3:30pm to discuss what you learned. 

<a href="http://www.noaa.gov/"><img width=200 align='center' src="http://www.nssl.noaa.gov/projects/debrisflow09/NOAA%20Circle.gif"></a>

Image From: https://www.ncdc.noaa.gov/data-access/land-based-station-data/land-based-datasets/us-climate-reference-network-uscrn

### Agenda for today's class (80 minutes)


1. [(10 minutes) NOAA Example](#NOAA_Example)
1. [(5 minutes) Installing Beautiful Soup](#Installing_Beautiful_Soup)
2. [(20 minutes) Presidential data example](#Presidential_data_example)
4. [(20 minutes) Dynamic Website example](#DynamicWebsites)
5. [(25 minutes) wrap-up Discussion](#Wrapup)

----
<a name="NOAA_Example"></a>

# 1. NOAA Example and Coding Standards.

We are going to start today's activity by doing a code review of a **_web spider_** program. 

&#9989; **<font color=red>DO THIS:</font>**  Download the [noaa_scrapper.py](./Files/noaa_scrapper.py) and [this jupyter notebook](./Files/0204-Web_Scraping.ipynb') annd put them in the same directory. Run the file via the following command:


    ---------------------------------------------------------------------------

    ModuleNotFoundError                       Traceback (most recent call last)

    <ipython-input-1-f8893b2e9fc2> in <module>
          2 import matplotlib.pyplot as plt
          3 
    ----> 4 from noaa_scraper import get_noaa_temperatures
    

    ModuleNotFoundError: No module named 'noaa_scraper'


&#9989; **<font color=red>DO THIS:</font>** Run the ```get_noaa_temperatures``` function as follows:


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-2-daf412f73ca4> in <module>
    ----> 1 air_temperatures = get_noaa_temperatures('http://www1.ncdc.noaa.gov/pub/data/uscrn/products/subhourly01/', 'Gaylord', 100)
          2 plt.plot(air_temperatures)
          3 # plt.axis([0,1000,-20,80])


    NameError: name 'get_noaa_temperatures' is not defined


&#9989; **<font color=red>DO THIS:</font>** With your group, do a code review of the contents of the **noaa_scraper.py** file and figure out what it does. What are the main part of this module and what do they do? Be prepared to discuss this with the class. 

Put your notes here

----
<a name="Installing_Beautiful_Soup"></a>

# 2. Installing Beautiful Soup

For this class we will be trying out [BeautifulSoup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/), a Python web parsing module. 

&#9989; **<font color=red>DO THIS:</font>** Install the ```beautifulsoup4``` library on your computer (the following will work on jupyterhub but should work anywhere).  When you are done, help your neighbor and raise your hand if you need help.

----
<a name="Presidential_data_example"></a>
# 3. Presidential data example
This second example is a **_web scraper_** program. Found this idea by reading the following blog post: https://blog.exploratory.io/scraping-us-presidents-list-from-web-and-transforming-it-to-be-useful-fff534470bb6

&#9989; **<font color=red>DO THIS:</font>** Click on the following link and review the page source with your teams.  Discuss which tags you need to look for to try and isolate the table data only.  Ideally we want to create a ```pandas table``` of this data:
https://www.loc.gov/rr/print/list/057_chron.html


Put notes on what you find here.

## Download and view html

The following code should download the above website and parse read it into a ```beautifulsoup``` object:

&#9989; **<font color=red>DO THIS:</font>** explore the ```soup``` variable using python functions such as; ```type```, ```dir``` and ```help```.


    <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"
            "http://www.w3.org/TR/html4/loose.dtd">
    <html>
     <!-- InstanceBegin template="/Templates/listguid.dwt" codeOutsideHTMLIsLocked="false" -->
     <head>
      <!-- InstanceBeginEditable name="doctitle" -->
      <title>
       Chronological List of Presidents, First Ladies, and Vice Presidents of the United States - Guides, Reference Aids, and Finding Aids (Prints andPhotographs Reading Room, Library of Congress)
      </title>
      <!-- InstanceEndEditable -->
      <!-- InstanceBeginEditable name="head" -->
      <meta content="American, presidents, U.S., United States" name="keywords"/>
      <meta content="Illustrations from the holdings of the Library of Congress Prints and Photographs Division on the subject of U.S. Presidents, First Ladies, and Vice Presidents" name="description"/>
      <meta content="text/html; charset=utf-8" http-equiv="Content-Type"/>
      <link href="../print.css" rel="stylesheet" type="text/css"/>
      <!-- InstanceEndEditable -->
      <script src="//assets.adobedtm.com/dac62e20b491e735c6b56e64c39134d8ee93f9cf/satelliteLib-6b47f831c184878d7338d4683ecf773a17973bb9.js">
      </script>
     </head>
     <body alink="#996666" background="../images/pnp-back.gif" link="#660066" text="#333333" vlink="#990066">
      <table border="0" cellpadding="0" cellspacing="0" width="760">
       <tr valign="top">
        <td bgcolor="#663366" colspan="2" height="25">
         <a href="#content" name="top">
          <img alt="Skip Navigation Links" border="0" height="1" src="../images/spacer-dkpurple.gif" width="1"/>
         </a>
         <a class="white" href="//www.loc.gov/">
          The
            Library of Congress
         </a>
         <span class="white-text">
          &gt;&gt;
         </span>
         <a class="white" href="//www.loc.gov/rr/">
          Researchers
         </a>
        </td>
       </tr>
       <!-- title graphic -->
       <tr>
        <td bgcolor="#663366" colspan="2">
         <img alt="Prints and Photographs Reading Room (Prints and Photographs Division)" height="37" src="../images/pnp-subtitle.gif" vspace="0" width="760"/>
        </td>
       </tr>
       <!-- spacer row -->
       <tr>
        <td bgcolor="#663366">
         <img alt="" height="1" src="../images/spacer-dkpurple.gif" width="310"/>
        </td>
        <td bgcolor="#663366">
         <img alt="" height="1" src="../images/spacer-dkpurple.gif" width="430"/>
        </td>
       </tr>
       <tr bgcolor="#EEEEEE">
        <td bgcolor="#DDDDDD">
         <a href="//www.loc.gov/rr/print/">
          Home
         </a>
         &gt;&gt;
         <!-- InstanceBeginEditable name="topbreadcrumb" -->
         <a href="listguid.html">
          Image Lists
         </a>
         &gt;&gt;
         <a href="057_intr.html">
          Presidents
         </a>
         <!-- InstanceEndEditable -->
        </td>
        <td align="right" bgcolor="#DDDDDD">
         <!-- InstanceBeginEditable name="topsearchbox" -->
         <form action="http://search.loc.gov:8765/query.html" method="GET" name="seek" style="margin-bottom:0;">
          <table bgcolor="#DDDDDD" border="0" cellpadding="4" cellspacing="0">
           <tr>
            <td align="right" height="32">
             <label for="find">
              Find
             </label>
            </td>
            <td>
             <input name="col" type="hidden" value="loc"/>
             <input id="find" maxlength="255" name="qt" size="15" style="font-family: monospace; font-size: 12px" tabindex="1" type="text" value=""/>
            </td>
            <td>
             <label for="in">
              in
             </label>
            </td>
            <td>
             <span class="drop-box">
              <select id="in" name="qp" size="1" tabindex="2">
               <option selected="" value="url:/rr/print/list/">
                Image Lists
               </option>
               <option value="url:/rr/print/">
                Prints
                          and Photographs Pages
               </option>
               <option value="url:/rr/ url:/cfbook/ url:/poetry/ url:/folklife/ url:/loc/kluge/">
                Researchers
                          Web Pages
               </option>
               <option value="">
                All Library
                          of Congress Pages
               </option>
              </select>
             </span>
            </td>
            <td align="left">
             <input align="top" alt="go" class="submit" name="submit" src="../images/go-button.gif" tabindex="3" type="image"/>
            </td>
           </tr>
          </table>
         </form>
         <!-- InstanceEndEditable -->
        </td>
       </tr>
       <!-- spacer row -->
       <tr>
        <td bgcolor="#663366">
         <img alt="" height="1" src="../images/spacer-dkpurple.gif" width="310"/>
        </td>
        <td bgcolor="#663366">
         <img alt="" height="1" src="../images/spacer-dkpurple.gif" width="430"/>
        </td>
       </tr>
       <!-- row to hold content table -->
       <tr>
        <td colspan="2">
         <!-- begin content table -->
         <a name="content">
         </a>
         <table border="0" cellpadding="6" cellspacing="6" width="680">
          <tr valign="top">
           <td width="100%">
            <!-- InstanceBeginEditable name="content" -->
            <h1>
             Chronological List of Presidents, First Ladies, and Vice Presidents of the United States
            </h1>
            <h2>
             Selected Images From the Collections of the Library of Congress
            </h2>
            <p>
             <strong>
              <a href="//www.loc.gov/rr/print/pphome.html">
               Prints and Photographs Division
              </a>
              , Library of
                  Congress, Washington, D.C., 20540-4730
             </strong>
            </p>
            <p>
             This chronological list contains entries for each president with his corresponding first lady and vice president. Note: Multiple entries appear for a president whenever there was a change in the office of vice president.
            </p>
            <p>
             <table border="1" cellpadding="4" cellspacing="2">
              <tr>
               <th width="55">
                YEAR
               </th>
               <th width="124">
                PRESIDENT
               </th>
               <th width="266">
                FIRST LADY
               </th>
               <th width="159">
                VICE PRESIDENT
               </th>
              </tr>
              <tr>
               <td>
                <b>
                 1789-1797
                </b>
               </td>
               <td>
                <a href="057_pra7.html#washington">
                 George Washington
                </a>
               </td>
               <td>
                <a href="058_fla4.html#washington">
                 Martha Washington
                </a>
               </td>
               <td>
                <a href="059_vpa1.html#adamsj">
                 John Adams
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1797-1801
                </b>
               </td>
               <td>
                <a href="057_pra1.html#adamsj">
                 John Adams
                </a>
               </td>
               <td>
                <a href="058_fla1.html#adamsa">
                 Abigail Adams
                </a>
               </td>
               <td>
                <a href="059_vpa3.html#jefferson">
                 Thomas Jefferson
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1801-1805
                </b>
               </td>
               <td>
                <a href="057_pra3.html#jefferson">
                 Thomas Jefferson
                </a>
               </td>
               <td>
                <p>
                 [Martha Wayles Skelton Jefferson
                 <br/>
                 died before Jefferson assumed office;
                 <br/>
                 no image of her in P&amp;P collections]
                </p>
               </td>
               <td>
                <a href="059_vpa1.html#burr">
                 Aaron Burr
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1805-1809
                </b>
               </td>
               <td>
                <a href="057_pra3.html#jefferson">
                 Thomas Jefferson
                </a>
               </td>
               <td>
                see above
               </td>
               <td>
                <a href="059_vpa1.html#clinton">
                 George Clinton
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1809-1812
                </b>
               </td>
               <td>
                <a href="057_pra4.html#madison">
                 James Madison
                </a>
               </td>
               <td>
                <a href="058_fla3.html#madison">
                 Dolley Madison
                </a>
               </td>
               <td>
                <a href="059_vpa1.html#clinton">
                 George Clinton
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1812-1813
                </b>
               </td>
               <td>
                <a href="057_pra4.html#madison">
                 James Madison
                </a>
               </td>
               <td>
                <a href="058_fla3.html#madison">
                 Dolley Madison
                </a>
               </td>
               <td>
                office vacant
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1813-1814
                </b>
               </td>
               <td>
                <a href="057_pra4.html#madison">
                 James Madison
                </a>
               </td>
               <td>
                <a href="058_fla3.html#madison">
                 Dolley Madison
                </a>
               </td>
               <td>
                <a href="059_vpa2.html#gerry">
                 Elbridge Gerry
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1814-1817
                </b>
               </td>
               <td>
                <a href="057_pra5.html#madison">
                 James Madison
                </a>
               </td>
               <td>
                <a href="058_fla3.html#madison">
                 Dolley Madison
                </a>
               </td>
               <td>
                office vacant
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1817-1825
                </b>
               </td>
               <td>
                <a href="057_pra5.html#monroe">
                 James Monroe
                </a>
               </td>
               <td>
                Elizabeth Kortright Monroe
                <br/>
                (no image)
               </td>
               <td>
                <a href="059_vpa4.html#tompkins">
                 Daniel D. Tompkins
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1825-1829
                </b>
               </td>
               <td>
                <a href="057_pra1.html#adamsjq">
                 John Quincy Adams
                </a>
               </td>
               <td>
                <a href="058_fla1.html#adamsl">
                 Louisa Catherine Adams
                </a>
               </td>
               <td>
                <a href="059_vpa1.html#calhoun">
                 John C. Calhoun
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1829-1832
                </b>
               </td>
               <td>
                <a href="057_pra3.html#jackson">
                 Andrew Jackson
                </a>
               </td>
               <td>
                <a href="058_fla3.html#jackson">
                 Rachel Jackson
                </a>
                [Rachel Donelson Jackson 
    died before Jackson assumed office and did not serve as first lady]
               </td>
               <td>
                <a href="059_vpa1.html#calhoun">
                 John C. Calhoun
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1833-1837
                </b>
               </td>
               <td>
                <a href="057_pra3.html#jackson">
                 Andrew Jackson
                </a>
               </td>
               <td>
                <a href="058_fla3.html#jackson">
                 Rachel Jackson
                </a>
                [Rachel Donelson Jackson 
    died before Jackson assumed office and did not serve as first lady]
               </td>
               <td>
                <a href="059_vpa4.html#vanburen">
                 Martin Van Buren
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1837-1841
                </b>
               </td>
               <td>
                <a href="057_pra7.html#vanburen">
                 Martin Van Buren
                </a>
               </td>
               <td>
                <a href="058_fla4.html#vanburen">
                 Hannah Hoes Van Buren
                </a>
               </td>
               <td>
                <a href="059_vpa3.html#johnsonr">
                 Richard M. Johnson
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1841
                </b>
               </td>
               <td>
                <a href="057_pra3.html#harrisonw">
                 William Henry Harrison
                </a>
               </td>
               <td>
                <a href="058_fla2.html#harrisona">
                 Anna Tuthill Symmes Harrison
                </a>
               </td>
               <td>
                <a href="059_vpa4.html#tyler">
                 John Tyler
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1841-1845
                </b>
               </td>
               <td>
                <a href="057_pra7.html#tyler">
                 John Tyler
                </a>
               </td>
               <td>
                Letitia Christian Tyler and
                <br/>
                Julia Gardiner Tyler (no images)
               </td>
               <td>
                office vacant
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1845-1849
                </b>
               </td>
               <td>
                <a href="057_pra5.html#polk">
                 James K. Polk
                </a>
               </td>
               <td>
                <a href="058_fla4.html#polk">
                 Sarah Childress Polk
                </a>
               </td>
               <td>
                <a href="059_vpa2.html#dallas">
                 George M. Dallas
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1849-1850
                </b>
               </td>
               <td>
                <a href="057_pra6.html#taylor">
                 Zachary Taylor
                </a>
               </td>
               <td>
                Margaret Mackall Smith Taylor
                <br/>
                (no image)
               </td>
               <td>
                <a href="059_vpa2.html#fillmore">
                 Millard Fillmore
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1850-1853
                </b>
               </td>
               <td>
                <a href="057_pra2.html#fillmore">
                 Millard Fillmore
                </a>
               </td>
               <td>
                <a href="058_fla2.html#fillmore">
                 Abigail Powers Fillmore
                </a>
               </td>
               <td>
                office vacant
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1853
                </b>
               </td>
               <td>
                <a href="057_pra5.html#pierce">
                 Franklin Pierce
                </a>
               </td>
               <td>
                <a href="058_fla4.html#pierce">
                 Jane M. Pierce
                </a>
               </td>
               <td>
                <a href="059_vpa3.html#king">
                 William R. King
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1853-1857
                </b>
               </td>
               <td>
                <a href="057_pra5.html#pierce">
                 Franklin Pierce
                </a>
               </td>
               <td>
                <a href="058_fla4.html#pierce">
                 Jane M. Pierce
                </a>
               </td>
               <td>
                office vacant
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1857-1861
                </b>
               </td>
               <td>
                <a href="057_pra1.html#buchanan">
                 James Buchanan
                </a>
               </td>
               <td>
                (never married)
               </td>
               <td>
                <a href="059_vpa1.html#breck">
                 John C. Breckinridge
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1861-1865
                </b>
               </td>
               <td>
                <a href="057_pra4.html#lincoln">
                 Abraham Lincoln
                </a>
               </td>
               <td>
                <a href="058_fla3.html#lincoln">
                 Mary Todd Lincoln
                </a>
               </td>
               <td>
                <a href="059_vpa2.html#hamlin">
                 Hannibal Hamlin
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1865
                </b>
               </td>
               <td>
                <a href="057_pra4.html#lincoln">
                 Abraham Lincoln
                </a>
               </td>
               <td>
                <a href="058_fla3.html#lincoln">
                 Mary Todd Lincoln
                </a>
               </td>
               <td>
                <a href="059_vpa3.html#johnsona">
                 Andrew Johnson
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1865-1869
                </b>
               </td>
               <td>
                <a href="057_pra4.html#johnsona">
                 Andrew Johnson
                </a>
               </td>
               <td>
                <a href="058_fla3.html#johnsone">
                 Eliza McCardle Johnson
                </a>
               </td>
               <td>
                office vacant
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1869-1873
                </b>
               </td>
               <td>
                <a href="057_pra2.html#grant">
                 Ulysses S. Grant
                </a>
               </td>
               <td>
                <a href="058_fla2.html#grant">
                 Julia Dent Grant
                </a>
               </td>
               <td>
                <a href="059_vpa1.html#colfax">
                 Schuyler Colfax
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1873-1875
                </b>
               </td>
               <td>
                <a href="057_pra2.html#grant">
                 Ulysses S. Grant
                </a>
               </td>
               <td>
                <a href="058_fla2.html#grant">
                 Julia Dent Grant
                </a>
               </td>
               <td>
                <a href="059_vpa4.html#wilson">
                 Henry Wilson
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1875-1877
                </b>
               </td>
               <td>
                <a href="057_pra2.html#grant">
                 Ulysses S. Grant
                </a>
               </td>
               <td>
                <a href="058_fla2.html#grant">
                 Julia Dent Grant
                </a>
               </td>
               <td>
                office vacant
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1877-1881
                </b>
               </td>
               <td>
                <a href="057_pra3.html#hayes">
                 Rutherford Birchard Hayes
                </a>
               </td>
               <td>
                <a href="058_fla2.html#hayes">
                 Lucy Webb Hayes
                </a>
               </td>
               <td>
                <a href="059_vpa4.html#wheeler">
                 William A. Wheeler
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1881
                </b>
               </td>
               <td>
                <a href="057_pra2.html#garfield">
                 James A. Garfield
                </a>
               </td>
               <td>
                <a href="058_fla2.html#garfield">
                 Lucretia Rudolph Garfield
                </a>
               </td>
               <td>
                <a href="059_vpa1.html#arthur">
                 Chester A. Arthur
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1881-1885
                </b>
               </td>
               <td>
                <a href="057_pra1.html#arthur">
                 Chester A. Arthur
                </a>
               </td>
               <td>
                <a href="058_fla1.html#arthur">
                 Ellen Lewis Herndon Arthur
                </a>
               </td>
               <td>
                office vacant
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1885
                </b>
               </td>
               <td>
                <a href="057_pra1.html#cleveland">
                 Grover Cleveland
                </a>
               </td>
               <td>
                <a href="058_fla1.html#cleveland">
                 Frances Folsom Cleveland
                </a>
               </td>
               <td>
                <a href="059_vpa2.html#hendricks">
                 Thomas A. Hendricks
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1885-1889
                </b>
               </td>
               <td>
                <a href="057_pra1.html#cleveland">
                 Grover Cleveland
                </a>
               </td>
               <td>
                <a href="058_fla1.html#cleveland">
                 Frances Folsom Cleveland
                </a>
               </td>
               <td>
                office vacant
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1889-1893
                </b>
               </td>
               <td>
                <a href="057_pra3.html#harrisonb">
                 Benjamin Harrison
                </a>
               </td>
               <td>
                <a href="058_fla2.html#harrisonc">
                 Caroline Lavinia Scott Harrison
                </a>
                <br/>
                <a href="058_fla2.html#harrisonm">
                 Mary Lord Harrison
                </a>
                <br/>
                [Harrison's second wife,
                <br/>
                but never a first lady]
               </td>
               <td>
                <a href="059_vpa3.html#morton">
                 Levi P. Morton
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1893-1897
                </b>
               </td>
               <td>
                <a href="057_pra1.html#cleveland">
                 Grover Cleveland
                </a>
               </td>
               <td>
                <a href="058_fla1.html#cleveland">
                 Frances Folsom Cleveland
                </a>
               </td>
               <td>
                <a href="059_vpa4.html#stevenson">
                 Adlai E. Stevenson
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1897-1899
                </b>
               </td>
               <td>
                <a href="057_pra4.html#mckinley">
                 William McKinley
                </a>
               </td>
               <td>
                <a href="058_fla3.html#mckinley">
                 Ida Saxton McKinley
                </a>
               </td>
               <td>
                <a href="059_vpa2.html#hobart">
                 Garret A. Hobart
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1899-1901
                </b>
               </td>
               <td>
                <a href="057_pra4.html#mckinley">
                 William McKinley
                </a>
               </td>
               <td>
                <a href="058_fla3.html#mckinley">
                 Ida Saxton McKinley
                </a>
               </td>
               <td>
                office vacant
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1901
                </b>
               </td>
               <td>
                <a href="057_pra4.html#mckinley">
                 William McKinley
                </a>
               </td>
               <td>
                <a href="058_fla3.html#mckinley">
                 Ida Saxton McKinley
                </a>
               </td>
               <td>
                <a href="059_vpa4.html#roosevelt">
                 Theodore Roosevelt
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1901-1905
                </b>
               </td>
               <td>
                <a href="057_pra5.html#rooseveltt">
                 Theodore Roosevelt
                </a>
               </td>
               <td>
                <a href="058_fla4.html#roosevelted">
                 Edith Kermit Carow Roosevelt
                </a>
               </td>
               <td>
                office vacant
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1905-1909
                </b>
               </td>
               <td>
                <a href="057_pra5.html#rooseveltt">
                 Theodore Roosevelt
                </a>
               </td>
               <td>
                <a href="058_fla4.html#roosevelted">
                 Edith Kermit Carow Roosevelt
                </a>
               </td>
               <td>
                <a href="059_vpa2.html#fairbanks">
                 Charles W. Fairbanks
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1909-1912
                </b>
               </td>
               <td>
                <a href="057_pra6.html#taft">
                 William H. Taft
                </a>
               </td>
               <td>
                <a href="058_fla4.html#taft">
                 Helen Herron Taft
                </a>
               </td>
               <td>
                <a href="059_vpa4.html#sherman">
                 James S. Sherman
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1912-1913
                </b>
               </td>
               <td>
                <a href="057_pra6.html#taft">
                 William H. Taft
                </a>
               </td>
               <td>
                <a href="058_fla4.html#taft">
                 Helen Herron Taft
                </a>
               </td>
               <td>
                office vacant
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1913-1921
                </b>
               </td>
               <td>
                <a href="057_pra7.html#wilson">
                 Woodrow Wilson
                </a>
               </td>
               <td>
                <a href="058_fla4.html#wilsonel">
                 Ellen Axson Wilson
                </a>
                and
                <br/>
                <a href="058_fla4.html#wilsoned">
                 Edith
          Bolling Galt Wilson
                </a>
               </td>
               <td>
                <a href="059_vpa3.html#marshall">
                 Thomas R. Marshall
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1921-1923
                </b>
               </td>
               <td>
                <a href="057_pra2.html#harding">
                 Warren G. Harding
                </a>
               </td>
               <td>
                <a href="058_fla2.html#harding">
                 Florence Kling Harding
                </a>
               </td>
               <td>
                <a href="059_vpa1.html#coolidge">
                 Calvin Coolidge
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1923-1925
                </b>
               </td>
               <td>
                <a href="057_pra2.html#coolidge">
                 Calvin Coolidge
                </a>
               </td>
               <td>
                <a href="058_fla1.html#coolidge">
                 Grace Goodhue Coolidge
                </a>
               </td>
               <td>
                office vacant
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1925-1929
                </b>
               </td>
               <td>
                <a href="057_pra2.html#coolidge">
                 Calvin Coolidge
                </a>
               </td>
               <td>
                <a href="058_fla1.html#coolidge">
                 Grace Goodhue Coolidge
                </a>
               </td>
               <td>
                <a href="059_vpa2.html#dawes">
                 Charles G. Dawes
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1929-1933
                </b>
               </td>
               <td>
                <a href="057_pra3.html#hoover">
                 Herbert Hoover
                </a>
               </td>
               <td>
                <a href="058_fla3.html#hoover">
                 Lou Henry Hoover
                </a>
               </td>
               <td>
                <a href="059_vpa2.html#curtis">
                 Charles Curtis
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1933-1941
                </b>
               </td>
               <td>
                <a href="057_pra5.html#rooseveltf">
                 Franklin D. Roosevelt
                </a>
               </td>
               <td>
                <a href="058_fla4.html#rooseveltel">
                 Eleanor Roosevelt
                </a>
               </td>
               <td>
                <a href="059_vpa2.html#garner">
                 John N. Garner
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1941-1945
                </b>
               </td>
               <td>
                <a href="057_pra5.html#rooseveltf">
                 Franklin D. Roosevelt
                </a>
               </td>
               <td>
                <a href="058_fla4.html#rooseveltel">
                 Eleanor Roosevelt
                </a>
               </td>
               <td>
                <a href="059_vpa4.html#wallace">
                 Henry A. Wallace
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1945
                </b>
               </td>
               <td>
                <a href="057_pra5.html#rooseveltf">
                 Franklin D. Roosevelt
                </a>
               </td>
               <td>
                <a href="058_fla4.html#rooseveltel">
                 Eleanor Roosevelt
                </a>
               </td>
               <td>
                <a href="059_vpa4.html#truman">
                 Harry S. Truman
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1945-1949
                </b>
               </td>
               <td>
                <a href="057_pra6.html#truman">
                 Harry S. Truman
                </a>
               </td>
               <td>
                <a href="058_fla4.html#truman">
                 Bess Wallace Truman
                </a>
               </td>
               <td>
                office vacant
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1949-1953
                </b>
               </td>
               <td>
                <a href="057_pra6.html#truman">
                 Harry S. Truman
                </a>
               </td>
               <td>
                <a href="058_fla4.html#truman">
                 Bess Wallace Truman
                </a>
               </td>
               <td>
                <a href="059_vpa1.html#barkley">
                 Barkley, Alben W.
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1953-1961
                </b>
               </td>
               <td>
                <a href="057_pra2.html#eisenhower">
                 Dwight D. Eisenhower
                </a>
               </td>
               <td>
                <a href="058_fla2.html#eisenhower">
                 Mamie Doud Eisenhower
                </a>
               </td>
               <td>
                <a href="059_vpa3.html#nixon">
                 Richard M. Nixon
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1961-1963
                </b>
               </td>
               <td>
                <a href="057_pra4.html#kennedy">
                 John F. Kennedy
                </a>
               </td>
               <td>
                <a href="058_fla3.html#kennedy">
                 Jacqueline Kennedy
                </a>
               </td>
               <td>
                <a href="059_vpa3.html#johnsonl">
                 Lyndon B. Johnson
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1963-1965
                </b>
               </td>
               <td>
                <a href="057_pra4.html#johnsonl">
                 Lyndon B. Johnson
                </a>
               </td>
               <td>
                <a href="058_fla3.html#johnsonl">
                 Lady Bird Johnson
                </a>
               </td>
               <td>
                office vacant
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1965-1969
                </b>
               </td>
               <td>
                <a href="057_pra4.html#johnsonl">
                 Lyndon B. Johnson
                </a>
               </td>
               <td>
                <a href="058_fla3.html#johnsonl">
                 Lady Bird Johnson
                </a>
               </td>
               <td>
                <a href="059_vpa3.html#humphrey">
                 Hubert H. Humphrey
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1969-1973
                </b>
               </td>
               <td>
                <a href="057_pra5.html#nixon">
                 Richard M. Nixon
                </a>
               </td>
               <td>
                <a href="058_fla3.html#nixon">
                 Pat Nixon
                </a>
               </td>
               <td>
                <a href="059_vpa1.html#agnew">
                 Spiro T. Agnew
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1973-1974
                </b>
               </td>
               <td>
                <a href="057_pra5.html#nixon">
                 Richard M. Nixon
                </a>
               </td>
               <td>
                <a href="058_fla3.html#nixon">
                 Pat Nixon
                </a>
               </td>
               <td>
                <a href="059_vpa2.html#ford">
                 Gerald R. Ford
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1974-1977
                </b>
               </td>
               <td>
                <a href="057_pra2.html#ford">
                 Gerald R. Ford
                </a>
               </td>
               <td>
                <a href="058_fla2.html#ford">
                 Betty Ford
                </a>
               </td>
               <td>
                <a href="059_vpa3.html#rockefeller">
                 Nelson Rockefeller
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1977-1981
                </b>
               </td>
               <td>
                <a href="057_pra1.html#carter">
                 Jimmy Carter
                </a>
               </td>
               <td>
                <a href="058_fla1.html#carter">
                 Rosalynn Carter
                </a>
               </td>
               <td>
                <a href="059_vpa3.html#mondale">
                 Walter F. Mondale
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1981-1989
                </b>
               </td>
               <td>
                <a href="057_pra5.html#reagan">
                 Ronald Reagan
                </a>
               </td>
               <td>
                <a href="058_fla4.html#reagan">
                 Nancy Reagan
                </a>
               </td>
               <td>
                <a href="059_vpa1.html#bush">
                 George Bush
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1989-1993
                </b>
               </td>
               <td>
                <a href="057_pra1.html#bush">
                 George Bush
                </a>
               </td>
               <td>
                <a href="058_fla1.html#bush">
                 Barbara Bush
                </a>
               </td>
               <td>
                <a href="059_vpa3.html#quayle">
                 Dan Quayle
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 1993-2001
                </b>
               </td>
               <td>
                <a href="057_pra2.html#clinton">
                 Bill Clinton
                </a>
               </td>
               <td>
                <a href="058_fla1.html#clinton">
                 Hillary Rodham Clinton
                </a>
               </td>
               <td>
                <a href="059_vpa2.html#gore">
                 Albert Gore
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 2001-2009
                </b>
               </td>
               <td>
                <a href="057_pra1.html#bushgw">
                 George W. Bush
                </a>
               </td>
               <td>
                <a href="058_fla1.html#bushl">
                 Laura Bush
                </a>
               </td>
               <td>
                <a href="../info/gwbushinfo.html">
                 Richard Cheney
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 2009-2017
                </b>
               </td>
               <td>
                <a href="057_pra5.html#obama">
                 Barack Obama
                </a>
               </td>
               <td>
                <a href="058_fla3.html#obama">
                 Michelle Obama
                </a>
               </td>
               <td>
                <a href="059_vpa1.html#biden">
                 Joseph R. Biden
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 2017-2021
                </b>
               </td>
               <td>
                <a href="057_pra6.html#trump">
                 Donald J. Trump
                </a>
               </td>
               <td>
                <a href="058_fla4.html#trump">
                 Melania Trump
                </a>
               </td>
               <td>
                <a href="059_vpa3.html#pence">
                 Mike Pence
                </a>
               </td>
              </tr>
              <tr>
               <td>
                <b>
                 2021-
                </b>
               </td>
               <td>
                <a href="057_pra1.html#biden">
                 Joseph R. Biden
                </a>
               </td>
               <td>
                <a href="058_fla1.html#biden">
                 Jill Biden
                </a>
               </td>
               <td>
                <a href="059_vpa2.html#harris">
                 Kamala Harris
                </a>
               </td>
              </tr>
             </table>
             <p>
              <!-- #BeginLibraryItem "/Library/pres-menu.lbi" -->
              <table bgcolor="#eeeeee" border="0" cellpadding="5" cellspacing="0" width="100%">
               <tr align="center">
                <td>
                 <strong>
                  Presidents:
                 </strong>
                 <a href="057_intr.html">
                  Introduction (Rights/Ordering
          Info.)
                 </a>
                 |
                 <a href="057_pra1.html">
                  Adams
            - Cleveland
                 </a>
                 |
                 <a href="057_pra2.html">
                  Clinton - Harding
                 </a>
                 <br/>
                 <a href="057_pra3.html">
                  Harrison
            - Jefferson
                 </a>
                 |
                 <a href="057_pra4.html">
                  Johnson - McKinley
                 </a>
                 |
                 <a href="057_pra5.html">
                  Monroe
              - Roosevelt
                 </a>
                 |
                 <a href="057_pra6.html">
                  Taft - Trump
                 </a>
                 |
                 <a href="057_pra7.html">
                  Tyler
                - Wilson
                 </a>
                 <br/>
                 <a href="057_pral.html">
                  List of names, Alphabetically
                 </a>
                 |
                 <a href="057_chron.html">
                  List
            of names, Chronologically
                 </a>
                </td>
               </tr>
              </table>
              <!-- #EndLibraryItem -->
              <!-- #BeginLibraryItem "/Library/fla-menu.lbi" -->
              <table bgcolor="#eeeeee" border="0" cellpadding="8" cellspacing="0" width="100%">
               <tr align="center">
                <td>
                 <strong>
                  First Ladies
                 </strong>
                 :
                 <a href="058_intr.html">
                  Introduction
          (Rights/Ordering Info.)
                 </a>
                 |
                 <a href="058_fla1.html">
                  Adams
            - Coolidge
                 </a>
                 |
                 <a href="058_fla2.html">
                  Eisenhower - Hoover
                  <br/>
                 </a>
                 <a href="058_fla3.html">
                  Jackson
                - Pierce
                 </a>
                 |
                 <a href="058_fla3.html">
                 </a>
                 <a href="058_fla4.html">
                  Polk - Wilson
                 </a>
                 |
                 <a href="058_flal.html">
                  List
                  of names, Alphabetically
                 </a>
                </td>
               </tr>
              </table>
              <!-- #EndLibraryItem -->
              <!-- #BeginLibraryItem "/Library/vicepres-menu.lbi" -->
              <table bgcolor="#eeeeee" border="0" cellpadding="5" cellspacing="0" width="100%">
               <tr align="center">
                <td>
                 <strong>
                  Vice Presidents:
                 </strong>
                 <a href="059_vp_intr.html">
                  Introduction (Rights/Ordering Info.)
                 </a>
                 |
                 <a href="059_vpa1.html">
                  Adams - Coolidge
                 </a>
                 |
                 <a href="059_vpa2.html">
                  Curtis - Hobart
                 </a>
                 <br/>
                 <a href="059_vpa3.html">
                  Humphrey - Rockefeller
                 </a>
                 |
                 <a href="059_vpa4.html">
                  Roosevelt - Wilson
                 </a>
                 <br/>
                 <a href="059_vp_alpha.html">
                  List of names, Alphabetically
                 </a>
                 |
                 <a href="057_chron.html">
                  List of names, Chronologically
                 </a>
                </td>
               </tr>
              </table>
              <!-- #EndLibraryItem -->
              <!-- #EndLibraryItem -->
              <!-- InstanceEndEditable -->
             </p>
            </p>
           </td>
          </tr>
          <tr valign="top">
           <td>
            <a href="#top">
             <img align="left" alt="Top of Page" border="0" height="22" src="../images/up-button.gif" width="22"/>
            </a>
            <a href="#top">
             Top
                  of Page
            </a>
           </td>
          </tr>
         </table>
         <!-- end content table -->
        </td>
       </tr>
       <!-- spacer row -->
       <tr>
        <td bgcolor="#663366">
         <img alt="" height="1" src="../images/spacer-dkpurple.gif" width="310"/>
        </td>
        <td bgcolor="#663366">
         <img alt="" height="1" src="../images/spacer-dkpurple.gif" width="430"/>
        </td>
       </tr>
       <tr bgcolor="#EEEEEE">
        <td bgcolor="#DDDDDD">
         <a href="//www.loc.gov/rr/print/">
          Home
         </a>
         &gt;&gt;
         <!-- InstanceBeginEditable name="bottombreadcrumb" -->
         <a href="listguid.html">
          Image Lists
         </a>
         &gt;&gt;
         <a href="057_intr.html">
          Presidents
         </a>
         <!-- InstanceEndEditable -->
        </td>
        <td align="right" bgcolor="#DDDDDD">
         <!-- InstanceBeginEditable name="bottomsearchbox" -->
         <form action="http://search.loc.gov:8765/query.html" method="GET" name="seek" style="margin-bottom:0;">
          <table bgcolor="#DDDDDD" border="0" cellpadding="4" cellspacing="0">
           <tr>
            <td align="right" height="32">
             <label for="find2">
              Find
             </label>
            </td>
            <td>
             <input name="col" type="hidden" value="loc"/>
             <input id="find2" maxlength="255" name="qt" size="15" style="font-family: monospace; font-size: 12px" tabindex="1" type="text" value=""/>
            </td>
            <td>
             <label for="in2">
              in
             </label>
            </td>
            <td>
             <span class="drop-box">
              <select id="in2" name="qp" size="1" tabindex="2">
               <option selected="" value="url:/rr/print/list/">
                Image Lists
               </option>
               <option value="url:/rr/print/">
                Prints and Photographs Pages
               </option>
               <option value="url:/rr/ url:/cfbook/ url:/poetry/ url:/folklife/ url:/loc/kluge/">
                Researchers
                    Web Pages
               </option>
               <option value="">
                All Library of Congress Pages
               </option>
              </select>
             </span>
            </td>
            <td align="left">
             <input align="top" alt="go" class="submit" name="submit" src="../images/go-button.gif" tabindex="3" type="image"/>
            </td>
           </tr>
          </table>
         </form>
         <!-- InstanceEndEditable -->
        </td>
       </tr>
       <tr>
        <td colspan="2">
         <table border="0" cellpadding="0" cellspacing="0" width="760">
          <tr>
           <td bgcolor="#663366" height="40" width="37%">
            <a class="white" href="//www.loc.gov/">
             The
              Library of Congress
            </a>
            <span class="white-text">
             &gt;&gt;
            </span>
            <a class="white" href="//www.loc.gov/rr/">
             Researchers
            </a>
            <br/>
            <span class="white-text">
             <!-- #BeginDate format:Am1 -->
             December 21, 2020
             <!-- #EndDate -->
            </span>
           </td>
           <td align="center" bgcolor="#663366" width="38%">
            <a class="white" href="//www.loc.gov/homepage/legal.html">
             Legal
            </a>
            <span class="white-text">
             |
            </span>
            <a class="white" href="//www.loc.gov/global/disclaim.html">
             External Link Disclaimer
            </a>
            <br/>
            <br/>
           </td>
           <td align="right" bgcolor="#663366" height="40" width="25%">
            <a class="white" href="//www.loc.gov/rr/askalib/ask-print.html">
             Contact
              Us:
            </a>
            <br/>
            <a class="white" href="//www.loc.gov/rr/askalib/ask-print.html">
             Ask
                a Librarian
            </a>
           </td>
          </tr>
         </table>
        </td>
       </tr>
      </table>
      <script>
       if(window['_satellite']){_satellite.pageBottom();}
      </script>
     </body>
     <!-- InstanceEnd -->
    </html>
    


## Find the Tables

Next, the following code finds all of the ```table``` sections in the website:




    bs4.element.ResultSet






    9



According to the above the results show that there are 9 ```table``` objects in the document.  We are just looking for the one that has our data in it. 



&#9989; **<font color=red>DO THIS:</font>** Find the table from the nine tables that has only the data we want. Make a variable ```table``` that only includes the information we want. Hint, it is not the first table which we can see by using the following code. 

    <table border="0" cellpadding="0" cellspacing="0" width="760">
     <tr valign="top">
      <td bgcolor="#663366" colspan="2" height="25">
       <a href="#content" name="top">
        <img alt="Skip Navigation Links" border="0" height="1" src="../images/spacer-dkpurple.gif" width="1"/>
       </a>
       <a class="white" href="//www.loc.gov/">
        The
            Library of Congress
       </a>
       <span class="white-text">
        &gt;&gt;
       </span>
       <a class="white" href="//www.loc.gov/rr/">
        Researchers
       </a>
      </td>
     </tr>
     <!-- title graphic -->
     <tr>
      <td bgcolor="#663366" colspan="2">
       <img alt="Prints and Photographs Reading Room (Prints and Photographs Division)" height="37" src="../images/pnp-subtitle.gif" vspace="0" width="760"/>
      </td>
     </tr>
     <!-- spacer row -->
     <tr>
      <td bgcolor="#663366">
       <img alt="" height="1" src="../images/spacer-dkpurple.gif" width="310"/>
      </td>
      <td bgcolor="#663366">
       <img alt="" height="1" src="../images/spacer-dkpurple.gif" width="430"/>
      </td>
     </tr>
     <tr bgcolor="#EEEEEE">
      <td bgcolor="#DDDDDD">
       <a href="//www.loc.gov/rr/print/">
        Home
       </a>
       &gt;&gt;
       <!-- InstanceBeginEditable name="topbreadcrumb" -->
       <a href="listguid.html">
        Image Lists
       </a>
       &gt;&gt;
       <a href="057_intr.html">
        Presidents
       </a>
       <!-- InstanceEndEditable -->
      </td>
      <td align="right" bgcolor="#DDDDDD">
       <!-- InstanceBeginEditable name="topsearchbox" -->
       <form action="http://search.loc.gov:8765/query.html" method="GET" name="seek" style="margin-bottom:0;">
        <table bgcolor="#DDDDDD" border="0" cellpadding="4" cellspacing="0">
         <tr>
          <td align="right" height="32">
           <label for="find">
            Find
           </label>
          </td>
          <td>
           <input name="col" type="hidden" value="loc"/>
           <input id="find" maxlength="255" name="qt" size="15" style="font-family: monospace; font-size: 12px" tabindex="1" type="text" value=""/>
          </td>
          <td>
           <label for="in">
            in
           </label>
          </td>
          <td>
           <span class="drop-box">
            <select id="in" name="qp" size="1" tabindex="2">
             <option selected="" value="url:/rr/print/list/">
              Image Lists
             </option>
             <option value="url:/rr/print/">
              Prints
                          and Photographs Pages
             </option>
             <option value="url:/rr/ url:/cfbook/ url:/poetry/ url:/folklife/ url:/loc/kluge/">
              Researchers
                          Web Pages
             </option>
             <option value="">
              All Library
                          of Congress Pages
             </option>
            </select>
           </span>
          </td>
          <td align="left">
           <input align="top" alt="go" class="submit" name="submit" src="../images/go-button.gif" tabindex="3" type="image"/>
          </td>
         </tr>
        </table>
       </form>
       <!-- InstanceEndEditable -->
      </td>
     </tr>
     <!-- spacer row -->
     <tr>
      <td bgcolor="#663366">
       <img alt="" height="1" src="../images/spacer-dkpurple.gif" width="310"/>
      </td>
      <td bgcolor="#663366">
       <img alt="" height="1" src="../images/spacer-dkpurple.gif" width="430"/>
      </td>
     </tr>
     <!-- row to hold content table -->
     <tr>
      <td colspan="2">
       <!-- begin content table -->
       <a name="content">
       </a>
       <table border="0" cellpadding="6" cellspacing="6" width="680">
        <tr valign="top">
         <td width="100%">
          <!-- InstanceBeginEditable name="content" -->
          <h1>
           Chronological List of Presidents, First Ladies, and Vice Presidents of the United States
          </h1>
          <h2>
           Selected Images From the Collections of the Library of Congress
          </h2>
          <p>
           <strong>
            <a href="//www.loc.gov/rr/print/pphome.html">
             Prints and Photographs Division
            </a>
            , Library of
                  Congress, Washington, D.C., 20540-4730
           </strong>
          </p>
          <p>
           This chronological list contains entries for each president with his corresponding first lady and vice president. Note: Multiple entries appear for a president whenever there was a change in the office of vice president.
          </p>
          <p>
           <table border="1" cellpadding="4" cellspacing="2">
            <tr>
             <th width="55">
              YEAR
             </th>
             <th width="124">
              PRESIDENT
             </th>
             <th width="266">
              FIRST LADY
             </th>
             <th width="159">
              VICE PRESIDENT
             </th>
            </tr>
            <tr>
             <td>
              <b>
               1789-1797
              </b>
             </td>
             <td>
              <a href="057_pra7.html#washington">
               George Washington
              </a>
             </td>
             <td>
              <a href="058_fla4.html#washington">
               Martha Washington
              </a>
             </td>
             <td>
              <a href="059_vpa1.html#adamsj">
               John Adams
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1797-1801
              </b>
             </td>
             <td>
              <a href="057_pra1.html#adamsj">
               John Adams
              </a>
             </td>
             <td>
              <a href="058_fla1.html#adamsa">
               Abigail Adams
              </a>
             </td>
             <td>
              <a href="059_vpa3.html#jefferson">
               Thomas Jefferson
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1801-1805
              </b>
             </td>
             <td>
              <a href="057_pra3.html#jefferson">
               Thomas Jefferson
              </a>
             </td>
             <td>
              <p>
               [Martha Wayles Skelton Jefferson
               <br/>
               died before Jefferson assumed office;
               <br/>
               no image of her in P&amp;P collections]
              </p>
             </td>
             <td>
              <a href="059_vpa1.html#burr">
               Aaron Burr
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1805-1809
              </b>
             </td>
             <td>
              <a href="057_pra3.html#jefferson">
               Thomas Jefferson
              </a>
             </td>
             <td>
              see above
             </td>
             <td>
              <a href="059_vpa1.html#clinton">
               George Clinton
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1809-1812
              </b>
             </td>
             <td>
              <a href="057_pra4.html#madison">
               James Madison
              </a>
             </td>
             <td>
              <a href="058_fla3.html#madison">
               Dolley Madison
              </a>
             </td>
             <td>
              <a href="059_vpa1.html#clinton">
               George Clinton
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1812-1813
              </b>
             </td>
             <td>
              <a href="057_pra4.html#madison">
               James Madison
              </a>
             </td>
             <td>
              <a href="058_fla3.html#madison">
               Dolley Madison
              </a>
             </td>
             <td>
              office vacant
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1813-1814
              </b>
             </td>
             <td>
              <a href="057_pra4.html#madison">
               James Madison
              </a>
             </td>
             <td>
              <a href="058_fla3.html#madison">
               Dolley Madison
              </a>
             </td>
             <td>
              <a href="059_vpa2.html#gerry">
               Elbridge Gerry
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1814-1817
              </b>
             </td>
             <td>
              <a href="057_pra5.html#madison">
               James Madison
              </a>
             </td>
             <td>
              <a href="058_fla3.html#madison">
               Dolley Madison
              </a>
             </td>
             <td>
              office vacant
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1817-1825
              </b>
             </td>
             <td>
              <a href="057_pra5.html#monroe">
               James Monroe
              </a>
             </td>
             <td>
              Elizabeth Kortright Monroe
              <br/>
              (no image)
             </td>
             <td>
              <a href="059_vpa4.html#tompkins">
               Daniel D. Tompkins
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1825-1829
              </b>
             </td>
             <td>
              <a href="057_pra1.html#adamsjq">
               John Quincy Adams
              </a>
             </td>
             <td>
              <a href="058_fla1.html#adamsl">
               Louisa Catherine Adams
              </a>
             </td>
             <td>
              <a href="059_vpa1.html#calhoun">
               John C. Calhoun
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1829-1832
              </b>
             </td>
             <td>
              <a href="057_pra3.html#jackson">
               Andrew Jackson
              </a>
             </td>
             <td>
              <a href="058_fla3.html#jackson">
               Rachel Jackson
              </a>
              [Rachel Donelson Jackson 
    died before Jackson assumed office and did not serve as first lady]
             </td>
             <td>
              <a href="059_vpa1.html#calhoun">
               John C. Calhoun
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1833-1837
              </b>
             </td>
             <td>
              <a href="057_pra3.html#jackson">
               Andrew Jackson
              </a>
             </td>
             <td>
              <a href="058_fla3.html#jackson">
               Rachel Jackson
              </a>
              [Rachel Donelson Jackson 
    died before Jackson assumed office and did not serve as first lady]
             </td>
             <td>
              <a href="059_vpa4.html#vanburen">
               Martin Van Buren
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1837-1841
              </b>
             </td>
             <td>
              <a href="057_pra7.html#vanburen">
               Martin Van Buren
              </a>
             </td>
             <td>
              <a href="058_fla4.html#vanburen">
               Hannah Hoes Van Buren
              </a>
             </td>
             <td>
              <a href="059_vpa3.html#johnsonr">
               Richard M. Johnson
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1841
              </b>
             </td>
             <td>
              <a href="057_pra3.html#harrisonw">
               William Henry Harrison
              </a>
             </td>
             <td>
              <a href="058_fla2.html#harrisona">
               Anna Tuthill Symmes Harrison
              </a>
             </td>
             <td>
              <a href="059_vpa4.html#tyler">
               John Tyler
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1841-1845
              </b>
             </td>
             <td>
              <a href="057_pra7.html#tyler">
               John Tyler
              </a>
             </td>
             <td>
              Letitia Christian Tyler and
              <br/>
              Julia Gardiner Tyler (no images)
             </td>
             <td>
              office vacant
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1845-1849
              </b>
             </td>
             <td>
              <a href="057_pra5.html#polk">
               James K. Polk
              </a>
             </td>
             <td>
              <a href="058_fla4.html#polk">
               Sarah Childress Polk
              </a>
             </td>
             <td>
              <a href="059_vpa2.html#dallas">
               George M. Dallas
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1849-1850
              </b>
             </td>
             <td>
              <a href="057_pra6.html#taylor">
               Zachary Taylor
              </a>
             </td>
             <td>
              Margaret Mackall Smith Taylor
              <br/>
              (no image)
             </td>
             <td>
              <a href="059_vpa2.html#fillmore">
               Millard Fillmore
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1850-1853
              </b>
             </td>
             <td>
              <a href="057_pra2.html#fillmore">
               Millard Fillmore
              </a>
             </td>
             <td>
              <a href="058_fla2.html#fillmore">
               Abigail Powers Fillmore
              </a>
             </td>
             <td>
              office vacant
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1853
              </b>
             </td>
             <td>
              <a href="057_pra5.html#pierce">
               Franklin Pierce
              </a>
             </td>
             <td>
              <a href="058_fla4.html#pierce">
               Jane M. Pierce
              </a>
             </td>
             <td>
              <a href="059_vpa3.html#king">
               William R. King
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1853-1857
              </b>
             </td>
             <td>
              <a href="057_pra5.html#pierce">
               Franklin Pierce
              </a>
             </td>
             <td>
              <a href="058_fla4.html#pierce">
               Jane M. Pierce
              </a>
             </td>
             <td>
              office vacant
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1857-1861
              </b>
             </td>
             <td>
              <a href="057_pra1.html#buchanan">
               James Buchanan
              </a>
             </td>
             <td>
              (never married)
             </td>
             <td>
              <a href="059_vpa1.html#breck">
               John C. Breckinridge
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1861-1865
              </b>
             </td>
             <td>
              <a href="057_pra4.html#lincoln">
               Abraham Lincoln
              </a>
             </td>
             <td>
              <a href="058_fla3.html#lincoln">
               Mary Todd Lincoln
              </a>
             </td>
             <td>
              <a href="059_vpa2.html#hamlin">
               Hannibal Hamlin
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1865
              </b>
             </td>
             <td>
              <a href="057_pra4.html#lincoln">
               Abraham Lincoln
              </a>
             </td>
             <td>
              <a href="058_fla3.html#lincoln">
               Mary Todd Lincoln
              </a>
             </td>
             <td>
              <a href="059_vpa3.html#johnsona">
               Andrew Johnson
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1865-1869
              </b>
             </td>
             <td>
              <a href="057_pra4.html#johnsona">
               Andrew Johnson
              </a>
             </td>
             <td>
              <a href="058_fla3.html#johnsone">
               Eliza McCardle Johnson
              </a>
             </td>
             <td>
              office vacant
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1869-1873
              </b>
             </td>
             <td>
              <a href="057_pra2.html#grant">
               Ulysses S. Grant
              </a>
             </td>
             <td>
              <a href="058_fla2.html#grant">
               Julia Dent Grant
              </a>
             </td>
             <td>
              <a href="059_vpa1.html#colfax">
               Schuyler Colfax
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1873-1875
              </b>
             </td>
             <td>
              <a href="057_pra2.html#grant">
               Ulysses S. Grant
              </a>
             </td>
             <td>
              <a href="058_fla2.html#grant">
               Julia Dent Grant
              </a>
             </td>
             <td>
              <a href="059_vpa4.html#wilson">
               Henry Wilson
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1875-1877
              </b>
             </td>
             <td>
              <a href="057_pra2.html#grant">
               Ulysses S. Grant
              </a>
             </td>
             <td>
              <a href="058_fla2.html#grant">
               Julia Dent Grant
              </a>
             </td>
             <td>
              office vacant
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1877-1881
              </b>
             </td>
             <td>
              <a href="057_pra3.html#hayes">
               Rutherford Birchard Hayes
              </a>
             </td>
             <td>
              <a href="058_fla2.html#hayes">
               Lucy Webb Hayes
              </a>
             </td>
             <td>
              <a href="059_vpa4.html#wheeler">
               William A. Wheeler
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1881
              </b>
             </td>
             <td>
              <a href="057_pra2.html#garfield">
               James A. Garfield
              </a>
             </td>
             <td>
              <a href="058_fla2.html#garfield">
               Lucretia Rudolph Garfield
              </a>
             </td>
             <td>
              <a href="059_vpa1.html#arthur">
               Chester A. Arthur
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1881-1885
              </b>
             </td>
             <td>
              <a href="057_pra1.html#arthur">
               Chester A. Arthur
              </a>
             </td>
             <td>
              <a href="058_fla1.html#arthur">
               Ellen Lewis Herndon Arthur
              </a>
             </td>
             <td>
              office vacant
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1885
              </b>
             </td>
             <td>
              <a href="057_pra1.html#cleveland">
               Grover Cleveland
              </a>
             </td>
             <td>
              <a href="058_fla1.html#cleveland">
               Frances Folsom Cleveland
              </a>
             </td>
             <td>
              <a href="059_vpa2.html#hendricks">
               Thomas A. Hendricks
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1885-1889
              </b>
             </td>
             <td>
              <a href="057_pra1.html#cleveland">
               Grover Cleveland
              </a>
             </td>
             <td>
              <a href="058_fla1.html#cleveland">
               Frances Folsom Cleveland
              </a>
             </td>
             <td>
              office vacant
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1889-1893
              </b>
             </td>
             <td>
              <a href="057_pra3.html#harrisonb">
               Benjamin Harrison
              </a>
             </td>
             <td>
              <a href="058_fla2.html#harrisonc">
               Caroline Lavinia Scott Harrison
              </a>
              <br/>
              <a href="058_fla2.html#harrisonm">
               Mary Lord Harrison
              </a>
              <br/>
              [Harrison's second wife,
              <br/>
              but never a first lady]
             </td>
             <td>
              <a href="059_vpa3.html#morton">
               Levi P. Morton
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1893-1897
              </b>
             </td>
             <td>
              <a href="057_pra1.html#cleveland">
               Grover Cleveland
              </a>
             </td>
             <td>
              <a href="058_fla1.html#cleveland">
               Frances Folsom Cleveland
              </a>
             </td>
             <td>
              <a href="059_vpa4.html#stevenson">
               Adlai E. Stevenson
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1897-1899
              </b>
             </td>
             <td>
              <a href="057_pra4.html#mckinley">
               William McKinley
              </a>
             </td>
             <td>
              <a href="058_fla3.html#mckinley">
               Ida Saxton McKinley
              </a>
             </td>
             <td>
              <a href="059_vpa2.html#hobart">
               Garret A. Hobart
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1899-1901
              </b>
             </td>
             <td>
              <a href="057_pra4.html#mckinley">
               William McKinley
              </a>
             </td>
             <td>
              <a href="058_fla3.html#mckinley">
               Ida Saxton McKinley
              </a>
             </td>
             <td>
              office vacant
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1901
              </b>
             </td>
             <td>
              <a href="057_pra4.html#mckinley">
               William McKinley
              </a>
             </td>
             <td>
              <a href="058_fla3.html#mckinley">
               Ida Saxton McKinley
              </a>
             </td>
             <td>
              <a href="059_vpa4.html#roosevelt">
               Theodore Roosevelt
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1901-1905
              </b>
             </td>
             <td>
              <a href="057_pra5.html#rooseveltt">
               Theodore Roosevelt
              </a>
             </td>
             <td>
              <a href="058_fla4.html#roosevelted">
               Edith Kermit Carow Roosevelt
              </a>
             </td>
             <td>
              office vacant
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1905-1909
              </b>
             </td>
             <td>
              <a href="057_pra5.html#rooseveltt">
               Theodore Roosevelt
              </a>
             </td>
             <td>
              <a href="058_fla4.html#roosevelted">
               Edith Kermit Carow Roosevelt
              </a>
             </td>
             <td>
              <a href="059_vpa2.html#fairbanks">
               Charles W. Fairbanks
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1909-1912
              </b>
             </td>
             <td>
              <a href="057_pra6.html#taft">
               William H. Taft
              </a>
             </td>
             <td>
              <a href="058_fla4.html#taft">
               Helen Herron Taft
              </a>
             </td>
             <td>
              <a href="059_vpa4.html#sherman">
               James S. Sherman
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1912-1913
              </b>
             </td>
             <td>
              <a href="057_pra6.html#taft">
               William H. Taft
              </a>
             </td>
             <td>
              <a href="058_fla4.html#taft">
               Helen Herron Taft
              </a>
             </td>
             <td>
              office vacant
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1913-1921
              </b>
             </td>
             <td>
              <a href="057_pra7.html#wilson">
               Woodrow Wilson
              </a>
             </td>
             <td>
              <a href="058_fla4.html#wilsonel">
               Ellen Axson Wilson
              </a>
              and
              <br/>
              <a href="058_fla4.html#wilsoned">
               Edith
          Bolling Galt Wilson
              </a>
             </td>
             <td>
              <a href="059_vpa3.html#marshall">
               Thomas R. Marshall
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1921-1923
              </b>
             </td>
             <td>
              <a href="057_pra2.html#harding">
               Warren G. Harding
              </a>
             </td>
             <td>
              <a href="058_fla2.html#harding">
               Florence Kling Harding
              </a>
             </td>
             <td>
              <a href="059_vpa1.html#coolidge">
               Calvin Coolidge
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1923-1925
              </b>
             </td>
             <td>
              <a href="057_pra2.html#coolidge">
               Calvin Coolidge
              </a>
             </td>
             <td>
              <a href="058_fla1.html#coolidge">
               Grace Goodhue Coolidge
              </a>
             </td>
             <td>
              office vacant
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1925-1929
              </b>
             </td>
             <td>
              <a href="057_pra2.html#coolidge">
               Calvin Coolidge
              </a>
             </td>
             <td>
              <a href="058_fla1.html#coolidge">
               Grace Goodhue Coolidge
              </a>
             </td>
             <td>
              <a href="059_vpa2.html#dawes">
               Charles G. Dawes
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1929-1933
              </b>
             </td>
             <td>
              <a href="057_pra3.html#hoover">
               Herbert Hoover
              </a>
             </td>
             <td>
              <a href="058_fla3.html#hoover">
               Lou Henry Hoover
              </a>
             </td>
             <td>
              <a href="059_vpa2.html#curtis">
               Charles Curtis
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1933-1941
              </b>
             </td>
             <td>
              <a href="057_pra5.html#rooseveltf">
               Franklin D. Roosevelt
              </a>
             </td>
             <td>
              <a href="058_fla4.html#rooseveltel">
               Eleanor Roosevelt
              </a>
             </td>
             <td>
              <a href="059_vpa2.html#garner">
               John N. Garner
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1941-1945
              </b>
             </td>
             <td>
              <a href="057_pra5.html#rooseveltf">
               Franklin D. Roosevelt
              </a>
             </td>
             <td>
              <a href="058_fla4.html#rooseveltel">
               Eleanor Roosevelt
              </a>
             </td>
             <td>
              <a href="059_vpa4.html#wallace">
               Henry A. Wallace
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1945
              </b>
             </td>
             <td>
              <a href="057_pra5.html#rooseveltf">
               Franklin D. Roosevelt
              </a>
             </td>
             <td>
              <a href="058_fla4.html#rooseveltel">
               Eleanor Roosevelt
              </a>
             </td>
             <td>
              <a href="059_vpa4.html#truman">
               Harry S. Truman
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1945-1949
              </b>
             </td>
             <td>
              <a href="057_pra6.html#truman">
               Harry S. Truman
              </a>
             </td>
             <td>
              <a href="058_fla4.html#truman">
               Bess Wallace Truman
              </a>
             </td>
             <td>
              office vacant
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1949-1953
              </b>
             </td>
             <td>
              <a href="057_pra6.html#truman">
               Harry S. Truman
              </a>
             </td>
             <td>
              <a href="058_fla4.html#truman">
               Bess Wallace Truman
              </a>
             </td>
             <td>
              <a href="059_vpa1.html#barkley">
               Barkley, Alben W.
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1953-1961
              </b>
             </td>
             <td>
              <a href="057_pra2.html#eisenhower">
               Dwight D. Eisenhower
              </a>
             </td>
             <td>
              <a href="058_fla2.html#eisenhower">
               Mamie Doud Eisenhower
              </a>
             </td>
             <td>
              <a href="059_vpa3.html#nixon">
               Richard M. Nixon
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1961-1963
              </b>
             </td>
             <td>
              <a href="057_pra4.html#kennedy">
               John F. Kennedy
              </a>
             </td>
             <td>
              <a href="058_fla3.html#kennedy">
               Jacqueline Kennedy
              </a>
             </td>
             <td>
              <a href="059_vpa3.html#johnsonl">
               Lyndon B. Johnson
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1963-1965
              </b>
             </td>
             <td>
              <a href="057_pra4.html#johnsonl">
               Lyndon B. Johnson
              </a>
             </td>
             <td>
              <a href="058_fla3.html#johnsonl">
               Lady Bird Johnson
              </a>
             </td>
             <td>
              office vacant
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1965-1969
              </b>
             </td>
             <td>
              <a href="057_pra4.html#johnsonl">
               Lyndon B. Johnson
              </a>
             </td>
             <td>
              <a href="058_fla3.html#johnsonl">
               Lady Bird Johnson
              </a>
             </td>
             <td>
              <a href="059_vpa3.html#humphrey">
               Hubert H. Humphrey
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1969-1973
              </b>
             </td>
             <td>
              <a href="057_pra5.html#nixon">
               Richard M. Nixon
              </a>
             </td>
             <td>
              <a href="058_fla3.html#nixon">
               Pat Nixon
              </a>
             </td>
             <td>
              <a href="059_vpa1.html#agnew">
               Spiro T. Agnew
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1973-1974
              </b>
             </td>
             <td>
              <a href="057_pra5.html#nixon">
               Richard M. Nixon
              </a>
             </td>
             <td>
              <a href="058_fla3.html#nixon">
               Pat Nixon
              </a>
             </td>
             <td>
              <a href="059_vpa2.html#ford">
               Gerald R. Ford
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1974-1977
              </b>
             </td>
             <td>
              <a href="057_pra2.html#ford">
               Gerald R. Ford
              </a>
             </td>
             <td>
              <a href="058_fla2.html#ford">
               Betty Ford
              </a>
             </td>
             <td>
              <a href="059_vpa3.html#rockefeller">
               Nelson Rockefeller
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1977-1981
              </b>
             </td>
             <td>
              <a href="057_pra1.html#carter">
               Jimmy Carter
              </a>
             </td>
             <td>
              <a href="058_fla1.html#carter">
               Rosalynn Carter
              </a>
             </td>
             <td>
              <a href="059_vpa3.html#mondale">
               Walter F. Mondale
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1981-1989
              </b>
             </td>
             <td>
              <a href="057_pra5.html#reagan">
               Ronald Reagan
              </a>
             </td>
             <td>
              <a href="058_fla4.html#reagan">
               Nancy Reagan
              </a>
             </td>
             <td>
              <a href="059_vpa1.html#bush">
               George Bush
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1989-1993
              </b>
             </td>
             <td>
              <a href="057_pra1.html#bush">
               George Bush
              </a>
             </td>
             <td>
              <a href="058_fla1.html#bush">
               Barbara Bush
              </a>
             </td>
             <td>
              <a href="059_vpa3.html#quayle">
               Dan Quayle
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               1993-2001
              </b>
             </td>
             <td>
              <a href="057_pra2.html#clinton">
               Bill Clinton
              </a>
             </td>
             <td>
              <a href="058_fla1.html#clinton">
               Hillary Rodham Clinton
              </a>
             </td>
             <td>
              <a href="059_vpa2.html#gore">
               Albert Gore
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               2001-2009
              </b>
             </td>
             <td>
              <a href="057_pra1.html#bushgw">
               George W. Bush
              </a>
             </td>
             <td>
              <a href="058_fla1.html#bushl">
               Laura Bush
              </a>
             </td>
             <td>
              <a href="../info/gwbushinfo.html">
               Richard Cheney
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               2009-2017
              </b>
             </td>
             <td>
              <a href="057_pra5.html#obama">
               Barack Obama
              </a>
             </td>
             <td>
              <a href="058_fla3.html#obama">
               Michelle Obama
              </a>
             </td>
             <td>
              <a href="059_vpa1.html#biden">
               Joseph R. Biden
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               2017-2021
              </b>
             </td>
             <td>
              <a href="057_pra6.html#trump">
               Donald J. Trump
              </a>
             </td>
             <td>
              <a href="058_fla4.html#trump">
               Melania Trump
              </a>
             </td>
             <td>
              <a href="059_vpa3.html#pence">
               Mike Pence
              </a>
             </td>
            </tr>
            <tr>
             <td>
              <b>
               2021-
              </b>
             </td>
             <td>
              <a href="057_pra1.html#biden">
               Joseph R. Biden
              </a>
             </td>
             <td>
              <a href="058_fla1.html#biden">
               Jill Biden
              </a>
             </td>
             <td>
              <a href="059_vpa2.html#harris">
               Kamala Harris
              </a>
             </td>
            </tr>
           </table>
           <p>
            <!-- #BeginLibraryItem "/Library/pres-menu.lbi" -->
            <table bgcolor="#eeeeee" border="0" cellpadding="5" cellspacing="0" width="100%">
             <tr align="center">
              <td>
               <strong>
                Presidents:
               </strong>
               <a href="057_intr.html">
                Introduction (Rights/Ordering
          Info.)
               </a>
               |
               <a href="057_pra1.html">
                Adams
            - Cleveland
               </a>
               |
               <a href="057_pra2.html">
                Clinton - Harding
               </a>
               <br/>
               <a href="057_pra3.html">
                Harrison
            - Jefferson
               </a>
               |
               <a href="057_pra4.html">
                Johnson - McKinley
               </a>
               |
               <a href="057_pra5.html">
                Monroe
              - Roosevelt
               </a>
               |
               <a href="057_pra6.html">
                Taft - Trump
               </a>
               |
               <a href="057_pra7.html">
                Tyler
                - Wilson
               </a>
               <br/>
               <a href="057_pral.html">
                List of names, Alphabetically
               </a>
               |
               <a href="057_chron.html">
                List
            of names, Chronologically
               </a>
              </td>
             </tr>
            </table>
            <!-- #EndLibraryItem -->
            <!-- #BeginLibraryItem "/Library/fla-menu.lbi" -->
            <table bgcolor="#eeeeee" border="0" cellpadding="8" cellspacing="0" width="100%">
             <tr align="center">
              <td>
               <strong>
                First Ladies
               </strong>
               :
               <a href="058_intr.html">
                Introduction
          (Rights/Ordering Info.)
               </a>
               |
               <a href="058_fla1.html">
                Adams
            - Coolidge
               </a>
               |
               <a href="058_fla2.html">
                Eisenhower - Hoover
                <br/>
               </a>
               <a href="058_fla3.html">
                Jackson
                - Pierce
               </a>
               |
               <a href="058_fla3.html">
               </a>
               <a href="058_fla4.html">
                Polk - Wilson
               </a>
               |
               <a href="058_flal.html">
                List
                  of names, Alphabetically
               </a>
              </td>
             </tr>
            </table>
            <!-- #EndLibraryItem -->
            <!-- #BeginLibraryItem "/Library/vicepres-menu.lbi" -->
            <table bgcolor="#eeeeee" border="0" cellpadding="5" cellspacing="0" width="100%">
             <tr align="center">
              <td>
               <strong>
                Vice Presidents:
               </strong>
               <a href="059_vp_intr.html">
                Introduction (Rights/Ordering Info.)
               </a>
               |
               <a href="059_vpa1.html">
                Adams - Coolidge
               </a>
               |
               <a href="059_vpa2.html">
                Curtis - Hobart
               </a>
               <br/>
               <a href="059_vpa3.html">
                Humphrey - Rockefeller
               </a>
               |
               <a href="059_vpa4.html">
                Roosevelt - Wilson
               </a>
               <br/>
               <a href="059_vp_alpha.html">
                List of names, Alphabetically
               </a>
               |
               <a href="057_chron.html">
                List of names, Chronologically
               </a>
              </td>
             </tr>
            </table>
            <!-- #EndLibraryItem -->
            <!-- #EndLibraryItem -->
            <!-- InstanceEndEditable -->
           </p>
          </p>
         </td>
        </tr>
        <tr valign="top">
         <td>
          <a href="#top">
           <img align="left" alt="Top of Page" border="0" height="22" src="../images/up-button.gif" width="22"/>
          </a>
          <a href="#top">
           Top
                  of Page
          </a>
         </td>
        </tr>
       </table>
       <!-- end content table -->
      </td>
     </tr>
     <!-- spacer row -->
     <tr>
      <td bgcolor="#663366">
       <img alt="" height="1" src="../images/spacer-dkpurple.gif" width="310"/>
      </td>
      <td bgcolor="#663366">
       <img alt="" height="1" src="../images/spacer-dkpurple.gif" width="430"/>
      </td>
     </tr>
     <tr bgcolor="#EEEEEE">
      <td bgcolor="#DDDDDD">
       <a href="//www.loc.gov/rr/print/">
        Home
       </a>
       &gt;&gt;
       <!-- InstanceBeginEditable name="bottombreadcrumb" -->
       <a href="listguid.html">
        Image Lists
       </a>
       &gt;&gt;
       <a href="057_intr.html">
        Presidents
       </a>
       <!-- InstanceEndEditable -->
      </td>
      <td align="right" bgcolor="#DDDDDD">
       <!-- InstanceBeginEditable name="bottomsearchbox" -->
       <form action="http://search.loc.gov:8765/query.html" method="GET" name="seek" style="margin-bottom:0;">
        <table bgcolor="#DDDDDD" border="0" cellpadding="4" cellspacing="0">
         <tr>
          <td align="right" height="32">
           <label for="find2">
            Find
           </label>
          </td>
          <td>
           <input name="col" type="hidden" value="loc"/>
           <input id="find2" maxlength="255" name="qt" size="15" style="font-family: monospace; font-size: 12px" tabindex="1" type="text" value=""/>
          </td>
          <td>
           <label for="in2">
            in
           </label>
          </td>
          <td>
           <span class="drop-box">
            <select id="in2" name="qp" size="1" tabindex="2">
             <option selected="" value="url:/rr/print/list/">
              Image Lists
             </option>
             <option value="url:/rr/print/">
              Prints and Photographs Pages
             </option>
             <option value="url:/rr/ url:/cfbook/ url:/poetry/ url:/folklife/ url:/loc/kluge/">
              Researchers
                    Web Pages
             </option>
             <option value="">
              All Library of Congress Pages
             </option>
            </select>
           </span>
          </td>
          <td align="left">
           <input align="top" alt="go" class="submit" name="submit" src="../images/go-button.gif" tabindex="3" type="image"/>
          </td>
         </tr>
        </table>
       </form>
       <!-- InstanceEndEditable -->
      </td>
     </tr>
     <tr>
      <td colspan="2">
       <table border="0" cellpadding="0" cellspacing="0" width="760">
        <tr>
         <td bgcolor="#663366" height="40" width="37%">
          <a class="white" href="//www.loc.gov/">
           The
              Library of Congress
          </a>
          <span class="white-text">
           &gt;&gt;
          </span>
          <a class="white" href="//www.loc.gov/rr/">
           Researchers
          </a>
          <br/>
          <span class="white-text">
           <!-- #BeginDate format:Am1 -->
           December 21, 2020
           <!-- #EndDate -->
          </span>
         </td>
         <td align="center" bgcolor="#663366" width="38%">
          <a class="white" href="//www.loc.gov/homepage/legal.html">
           Legal
          </a>
          <span class="white-text">
           |
          </span>
          <a class="white" href="//www.loc.gov/global/disclaim.html">
           External Link Disclaimer
          </a>
          <br/>
          <br/>
         </td>
         <td align="right" bgcolor="#663366" height="40" width="25%">
          <a class="white" href="//www.loc.gov/rr/askalib/ask-print.html">
           Contact
              Us:
          </a>
          <br/>
          <a class="white" href="//www.loc.gov/rr/askalib/ask-print.html">
           Ask
                a Librarian
          </a>
         </td>
        </tr>
       </table>
      </td>
     </tr>
    </table>
    


## Parse out all the rows

The rows of a table are determined by the ```tr``` (table row) tag and the columns are determined by the ```td```. The following code can find all of the rows in the table:




    [<tr valign="top">
     <td bgcolor="#663366" colspan="2" height="25"><a href="#content" name="top"><img alt="Skip Navigation Links" border="0" height="1" src="../images/spacer-dkpurple.gif" width="1"/></a>  <a class="white" href="//www.loc.gov/">The
             Library of Congress</a> <span class="white-text">&gt;&gt;</span> <a class="white" href="//www.loc.gov/rr/">Researchers</a></td>
     </tr>,
     <tr>
     <td bgcolor="#663366" colspan="2"><img alt="Prints and Photographs Reading Room (Prints and Photographs Division)" height="37" src="../images/pnp-subtitle.gif" vspace="0" width="760"/></td>
     </tr>,
     <tr>
     <td bgcolor="#663366"><img alt="" height="1" src="../images/spacer-dkpurple.gif" width="310"/></td>
     <td bgcolor="#663366"><img alt="" height="1" src="../images/spacer-dkpurple.gif" width="430"/></td>
     </tr>,
     <tr bgcolor="#EEEEEE">
     <td bgcolor="#DDDDDD">  <a href="//www.loc.gov/rr/print/">Home</a> &gt;&gt; <!-- InstanceBeginEditable name="topbreadcrumb" -->
     <a href="listguid.html">Image Lists</a> &gt;&gt; <a href="057_intr.html">Presidents</a><!-- InstanceEndEditable --></td>
     <td align="right" bgcolor="#DDDDDD">
     <!-- InstanceBeginEditable name="topsearchbox" -->
     <form action="http://search.loc.gov:8765/query.html" method="GET" name="seek" style="margin-bottom:0;">
     <table bgcolor="#DDDDDD" border="0" cellpadding="4" cellspacing="0">
     <tr>
     <td align="right" height="32"><label for="find">Find</label>
     </td>
     <td><input name="col" type="hidden" value="loc"/>
     <input id="find" maxlength="255" name="qt" size="15" style="font-family: monospace; font-size: 12px" tabindex="1" type="text" value=""/>
     </td>
     <td><label for="in">in</label>
     </td>
     <td><span class="drop-box">
     <select id="in" name="qp" size="1" tabindex="2">
     <option selected="" value="url:/rr/print/list/">Image Lists</option>
     <option value="url:/rr/print/">Prints
                           and Photographs Pages</option>
     <option value="url:/rr/ url:/cfbook/ url:/poetry/ url:/folklife/ url:/loc/kluge/">Researchers
                           Web Pages</option>
     <option value="">All Library
                           of Congress Pages</option>
     </select>
     </span></td>
     <td align="left"><input align="top" alt="go" class="submit" name="submit" src="../images/go-button.gif" tabindex="3" type="image"/>
     </td>
     </tr>
     </table>
     </form>
     <!-- InstanceEndEditable --></td>
     </tr>,
     <tr>
     <td align="right" height="32"><label for="find">Find</label>
     </td>
     <td><input name="col" type="hidden" value="loc"/>
     <input id="find" maxlength="255" name="qt" size="15" style="font-family: monospace; font-size: 12px" tabindex="1" type="text" value=""/>
     </td>
     <td><label for="in">in</label>
     </td>
     <td><span class="drop-box">
     <select id="in" name="qp" size="1" tabindex="2">
     <option selected="" value="url:/rr/print/list/">Image Lists</option>
     <option value="url:/rr/print/">Prints
                           and Photographs Pages</option>
     <option value="url:/rr/ url:/cfbook/ url:/poetry/ url:/folklife/ url:/loc/kluge/">Researchers
                           Web Pages</option>
     <option value="">All Library
                           of Congress Pages</option>
     </select>
     </span></td>
     <td align="left"><input align="top" alt="go" class="submit" name="submit" src="../images/go-button.gif" tabindex="3" type="image"/>
     </td>
     </tr>,
     <tr>
     <td bgcolor="#663366"><img alt="" height="1" src="../images/spacer-dkpurple.gif" width="310"/></td>
     <td bgcolor="#663366"><img alt="" height="1" src="../images/spacer-dkpurple.gif" width="430"/></td>
     </tr>,
     <tr>
     <td colspan="2">
     <!-- begin content table -->
     <a name="content"></a> <table border="0" cellpadding="6" cellspacing="6" width="680">
     <tr valign="top">
     <td width="100%"> <!-- InstanceBeginEditable name="content" -->
     <h1>Chronological List of Presidents, First Ladies, and Vice Presidents of the United States</h1>
     <h2>Selected Images From the Collections of the Library of Congress</h2>
     <p><strong><a href="//www.loc.gov/rr/print/pphome.html">Prints and Photographs Division</a>, Library of
                   Congress, Washington, D.C., 20540-4730</strong>
     </p>
     <p>
     This chronological list contains entries for each president with his corresponding first lady and vice president. Note: Multiple entries appear for a president whenever there was a change in the office of vice president.
     </p>
     <p>
     <table border="1" cellpadding="4" cellspacing="2">
     <tr>
     <th width="55">YEAR</th>
     <th width="124">PRESIDENT</th>
     <th width="266">FIRST LADY</th>
     <th width="159">VICE PRESIDENT</th>
     </tr>
     <tr>
     <td><b>1789-1797</b></td>
     <td><a href="057_pra7.html#washington">George Washington</a></td>
     <td><a href="058_fla4.html#washington">Martha Washington</a></td>
     <td><a href="059_vpa1.html#adamsj">John Adams</a></td>
     </tr>
     <tr>
     <td><b>1797-1801</b></td>
     <td><a href="057_pra1.html#adamsj">John Adams</a></td>
     <td><a href="058_fla1.html#adamsa">Abigail Adams</a></td>
     <td><a href="059_vpa3.html#jefferson">Thomas Jefferson</a></td>
     </tr>
     <tr>
     <td><b>1801-1805</b></td>
     <td><a href="057_pra3.html#jefferson">Thomas Jefferson</a></td>
     <td><p>[Martha Wayles Skelton Jefferson <br/>
         died before Jefferson assumed office;<br/>
     no image of her in P&amp;P collections]</p></td>
     <td><a href="059_vpa1.html#burr">Aaron Burr</a></td>
     </tr>
     <tr>
     <td><b>1805-1809</b></td>
     <td><a href="057_pra3.html#jefferson">Thomas Jefferson</a></td>
     <td>see above</td>
     <td><a href="059_vpa1.html#clinton">George Clinton</a></td>
     </tr>
     <tr>
     <td><b>1809-1812</b></td>
     <td><a href="057_pra4.html#madison">James Madison</a></td>
     <td><a href="058_fla3.html#madison">Dolley Madison</a></td>
     <td><a href="059_vpa1.html#clinton">George Clinton</a></td>
     </tr>
     <tr>
     <td><b>1812-1813</b></td>
     <td><a href="057_pra4.html#madison">James Madison</a></td>
     <td><a href="058_fla3.html#madison">Dolley Madison</a></td>
     <td>office vacant</td>
     </tr>
     <tr>
     <td><b>1813-1814</b></td>
     <td><a href="057_pra4.html#madison">James Madison</a></td>
     <td><a href="058_fla3.html#madison">Dolley Madison</a></td>
     <td><a href="059_vpa2.html#gerry">Elbridge Gerry</a></td>
     </tr>
     <tr>
     <td><b>1814-1817</b></td>
     <td><a href="057_pra5.html#madison">James Madison</a></td>
     <td><a href="058_fla3.html#madison">Dolley Madison</a></td>
     <td>office vacant</td>
     </tr>
     <tr>
     <td><b>1817-1825</b></td>
     <td><a href="057_pra5.html#monroe">James Monroe</a></td>
     <td>Elizabeth Kortright Monroe<br/>
        (no image)</td>
     <td><a href="059_vpa4.html#tompkins">Daniel D. Tompkins</a></td>
     </tr>
     <tr>
     <td><b>1825-1829</b></td>
     <td><a href="057_pra1.html#adamsjq">John Quincy Adams</a></td>
     <td><a href="058_fla1.html#adamsl">Louisa Catherine Adams</a></td>
     <td><a href="059_vpa1.html#calhoun">John C. Calhoun</a></td>
     </tr>
     <tr>
     <td><b>1829-1832</b></td>
     <td><a href="057_pra3.html#jackson">Andrew Jackson</a></td>
     <td><a href="058_fla3.html#jackson">Rachel Jackson</a> [Rachel Donelson Jackson 
     died before Jackson assumed office and did not serve as first lady]</td>
     <td><a href="059_vpa1.html#calhoun">John C. Calhoun</a></td>
     </tr>
     <tr>
     <td><b>1833-1837</b></td>
     <td><a href="057_pra3.html#jackson">Andrew Jackson</a></td>
     <td><a href="058_fla3.html#jackson">Rachel Jackson</a> [Rachel Donelson Jackson 
     died before Jackson assumed office and did not serve as first lady]</td>
     <td><a href="059_vpa4.html#vanburen">Martin Van Buren</a></td>
     </tr>
     <tr>
     <td><b>1837-1841</b></td>
     <td><a href="057_pra7.html#vanburen">Martin Van Buren</a></td>
     <td><a href="058_fla4.html#vanburen">Hannah Hoes Van Buren</a></td>
     <td><a href="059_vpa3.html#johnsonr">Richard M. Johnson</a></td>
     </tr>
     <tr>
     <td><b>1841</b></td>
     <td><a href="057_pra3.html#harrisonw">William Henry Harrison</a></td>
     <td><a href="058_fla2.html#harrisona">Anna Tuthill Symmes Harrison</a></td>
     <td><a href="059_vpa4.html#tyler">John Tyler</a></td>
     </tr>
     <tr>
     <td><b>1841-1845</b></td>
     <td><a href="057_pra7.html#tyler">John Tyler</a></td>
     <td>Letitia Christian Tyler and<br/> Julia Gardiner Tyler (no images)</td>
     <td>office vacant</td>
     </tr>
     <tr>
     <td><b>1845-1849</b></td>
     <td><a href="057_pra5.html#polk">James K. Polk</a></td>
     <td><a href="058_fla4.html#polk">Sarah Childress Polk</a></td>
     <td><a href="059_vpa2.html#dallas">George M. Dallas</a></td>
     </tr>
     <tr>
     <td><b>1849-1850</b></td>
     <td><a href="057_pra6.html#taylor">Zachary Taylor</a></td>
     <td>Margaret Mackall Smith Taylor<br/>
        (no image)</td>
     <td><a href="059_vpa2.html#fillmore">Millard Fillmore</a></td>
     </tr>
     <tr>
     <td><b>1850-1853</b></td>
     <td><a href="057_pra2.html#fillmore">Millard Fillmore</a></td>
     <td><a href="058_fla2.html#fillmore">Abigail Powers Fillmore</a></td>
     <td>office vacant</td>
     </tr>
     <tr>
     <td><b>1853</b></td>
     <td><a href="057_pra5.html#pierce">Franklin Pierce</a></td>
     <td><a href="058_fla4.html#pierce">Jane M. Pierce</a></td>
     <td><a href="059_vpa3.html#king">William R. King</a></td>
     </tr>
     <tr>
     <td><b>1853-1857</b></td>
     <td><a href="057_pra5.html#pierce">Franklin Pierce</a></td>
     <td><a href="058_fla4.html#pierce">Jane M. Pierce</a></td>
     <td>office vacant</td>
     </tr>
     <tr>
     <td><b>1857-1861</b></td>
     <td><a href="057_pra1.html#buchanan">James Buchanan</a></td>
     <td>(never married)</td>
     <td><a href="059_vpa1.html#breck">John C. Breckinridge</a></td>
     </tr>
     <tr>
     <td><b>1861-1865</b></td>
     <td><a href="057_pra4.html#lincoln">Abraham Lincoln</a></td>
     <td><a href="058_fla3.html#lincoln">Mary Todd Lincoln</a></td>
     <td><a href="059_vpa2.html#hamlin">Hannibal Hamlin</a></td>
     </tr>
     <tr>
     <td><b>1865</b></td>
     <td><a href="057_pra4.html#lincoln">Abraham Lincoln</a></td>
     <td><a href="058_fla3.html#lincoln">Mary Todd Lincoln</a></td>
     <td><a href="059_vpa3.html#johnsona">Andrew Johnson</a></td>
     </tr>
     <tr>
     <td><b>1865-1869</b></td>
     <td><a href="057_pra4.html#johnsona">Andrew Johnson</a></td>
     <td><a href="058_fla3.html#johnsone">Eliza McCardle Johnson</a></td>
     <td>office vacant</td>
     </tr>
     <tr>
     <td><b>1869-1873</b></td>
     <td><a href="057_pra2.html#grant">Ulysses S. Grant</a></td>
     <td><a href="058_fla2.html#grant">Julia Dent Grant</a></td>
     <td><a href="059_vpa1.html#colfax">Schuyler Colfax</a></td>
     </tr>
     <tr>
     <td><b>1873-1875</b></td>
     <td><a href="057_pra2.html#grant">Ulysses S. Grant</a></td>
     <td><a href="058_fla2.html#grant">Julia Dent Grant</a></td>
     <td><a href="059_vpa4.html#wilson">Henry Wilson</a></td>
     </tr>
     <tr>
     <td><b>1875-1877</b></td>
     <td><a href="057_pra2.html#grant">Ulysses S. Grant</a></td>
     <td><a href="058_fla2.html#grant">Julia Dent Grant</a></td>
     <td>office vacant</td>
     </tr>
     <tr>
     <td><b>1877-1881</b></td>
     <td><a href="057_pra3.html#hayes">Rutherford Birchard Hayes</a></td>
     <td><a href="058_fla2.html#hayes">Lucy Webb Hayes</a></td>
     <td><a href="059_vpa4.html#wheeler">William A. Wheeler</a></td>
     </tr>
     <tr>
     <td><b>1881</b></td>
     <td><a href="057_pra2.html#garfield">James A. Garfield</a></td>
     <td><a href="058_fla2.html#garfield">Lucretia Rudolph Garfield</a></td>
     <td><a href="059_vpa1.html#arthur">Chester A. Arthur</a></td>
     </tr>
     <tr>
     <td><b>1881-1885</b></td>
     <td><a href="057_pra1.html#arthur">Chester A. Arthur</a></td>
     <td><a href="058_fla1.html#arthur">Ellen Lewis Herndon Arthur</a></td>
     <td>office vacant</td>
     </tr>
     <tr>
     <td><b>1885</b></td>
     <td><a href="057_pra1.html#cleveland">Grover Cleveland</a></td>
     <td><a href="058_fla1.html#cleveland">Frances Folsom Cleveland</a></td>
     <td><a href="059_vpa2.html#hendricks">Thomas A. Hendricks</a></td>
     </tr>
     <tr>
     <td><b>1885-1889</b></td>
     <td><a href="057_pra1.html#cleveland">Grover Cleveland</a></td>
     <td><a href="058_fla1.html#cleveland">Frances Folsom Cleveland</a></td>
     <td>office vacant</td>
     </tr>
     <tr>
     <td><b>1889-1893</b></td>
     <td><a href="057_pra3.html#harrisonb">Benjamin Harrison</a></td>
     <td><a href="058_fla2.html#harrisonc">Caroline Lavinia Scott Harrison</a><br/>
     <a href="058_fla2.html#harrisonm">Mary Lord Harrison</a><br/>
        [Harrison's second wife,<br/>
         but never a first lady]</td>
     <td><a href="059_vpa3.html#morton">Levi P. Morton</a></td>
     </tr>
     <tr>
     <td><b>1893-1897</b></td>
     <td><a href="057_pra1.html#cleveland">Grover Cleveland</a></td>
     <td><a href="058_fla1.html#cleveland">Frances Folsom Cleveland</a></td>
     <td><a href="059_vpa4.html#stevenson">Adlai E. Stevenson</a></td>
     </tr>
     <tr>
     <td><b>1897-1899</b></td>
     <td><a href="057_pra4.html#mckinley">William McKinley</a></td>
     <td><a href="058_fla3.html#mckinley">Ida Saxton McKinley</a></td>
     <td><a href="059_vpa2.html#hobart">Garret A. Hobart</a></td>
     </tr>
     <tr>
     <td><b>1899-1901</b></td>
     <td><a href="057_pra4.html#mckinley">William McKinley</a></td>
     <td><a href="058_fla3.html#mckinley">Ida Saxton McKinley</a></td>
     <td>office vacant</td>
     </tr>
     <tr>
     <td><b>1901</b></td>
     <td><a href="057_pra4.html#mckinley">William McKinley</a></td>
     <td><a href="058_fla3.html#mckinley">Ida Saxton McKinley</a></td>
     <td><a href="059_vpa4.html#roosevelt">Theodore Roosevelt</a></td>
     </tr>
     <tr>
     <td><b>1901-1905</b></td>
     <td><a href="057_pra5.html#rooseveltt">Theodore Roosevelt</a></td>
     <td><a href="058_fla4.html#roosevelted">Edith Kermit Carow Roosevelt</a></td>
     <td>office vacant</td>
     </tr>
     <tr>
     <td><b>1905-1909</b></td>
     <td><a href="057_pra5.html#rooseveltt">Theodore Roosevelt</a></td>
     <td><a href="058_fla4.html#roosevelted">Edith Kermit Carow Roosevelt</a></td>
     <td><a href="059_vpa2.html#fairbanks">Charles W. Fairbanks</a></td>
     </tr>
     <tr>
     <td><b>1909-1912</b></td>
     <td><a href="057_pra6.html#taft">William H. Taft</a></td>
     <td><a href="058_fla4.html#taft">Helen Herron Taft</a></td>
     <td><a href="059_vpa4.html#sherman">James S. Sherman</a></td>
     </tr>
     <tr>
     <td><b>1912-1913</b></td>
     <td><a href="057_pra6.html#taft">William H. Taft</a></td>
     <td><a href="058_fla4.html#taft">Helen Herron Taft</a></td>
     <td>office vacant</td>
     </tr>
     <tr>
     <td><b>1913-1921</b></td>
     <td><a href="057_pra7.html#wilson">Woodrow Wilson</a></td>
     <td><a href="058_fla4.html#wilsonel">Ellen Axson Wilson</a> and <br/>
     <a href="058_fla4.html#wilsoned">Edith
           Bolling Galt Wilson</a></td>
     <td><a href="059_vpa3.html#marshall">Thomas R. Marshall</a></td>
     </tr>
     <tr>
     <td><b>1921-1923</b></td>
     <td><a href="057_pra2.html#harding">Warren G. Harding</a></td>
     <td><a href="058_fla2.html#harding">Florence Kling Harding</a></td>
     <td><a href="059_vpa1.html#coolidge">Calvin Coolidge</a></td>
     </tr>
     <tr>
     <td><b>1923-1925</b></td>
     <td><a href="057_pra2.html#coolidge">Calvin Coolidge</a></td>
     <td><a href="058_fla1.html#coolidge">Grace Goodhue Coolidge</a></td>
     <td>office vacant</td>
     </tr>
     <tr>
     <td><b>1925-1929</b></td>
     <td><a href="057_pra2.html#coolidge">Calvin Coolidge</a></td>
     <td><a href="058_fla1.html#coolidge">Grace Goodhue Coolidge</a></td>
     <td><a href="059_vpa2.html#dawes">Charles G. Dawes</a></td>
     </tr>
     <tr>
     <td><b>1929-1933</b></td>
     <td><a href="057_pra3.html#hoover">Herbert Hoover</a></td>
     <td><a href="058_fla3.html#hoover">Lou Henry Hoover</a></td>
     <td><a href="059_vpa2.html#curtis">Charles Curtis</a></td>
     </tr>
     <tr>
     <td><b>1933-1941</b></td>
     <td><a href="057_pra5.html#rooseveltf">Franklin D. Roosevelt</a></td>
     <td><a href="058_fla4.html#rooseveltel">Eleanor Roosevelt</a></td>
     <td><a href="059_vpa2.html#garner">John N. Garner</a></td>
     </tr>
     <tr>
     <td><b>1941-1945</b></td>
     <td><a href="057_pra5.html#rooseveltf">Franklin D. Roosevelt</a></td>
     <td><a href="058_fla4.html#rooseveltel">Eleanor Roosevelt</a></td>
     <td><a href="059_vpa4.html#wallace">Henry A. Wallace</a></td>
     </tr>
     <tr>
     <td><b>1945</b></td>
     <td><a href="057_pra5.html#rooseveltf">Franklin D. Roosevelt</a></td>
     <td><a href="058_fla4.html#rooseveltel">Eleanor Roosevelt</a></td>
     <td><a href="059_vpa4.html#truman">Harry S. Truman</a></td>
     </tr>
     <tr>
     <td><b>1945-1949</b></td>
     <td><a href="057_pra6.html#truman">Harry S. Truman</a></td>
     <td><a href="058_fla4.html#truman">Bess Wallace Truman</a></td>
     <td>office vacant</td>
     </tr>
     <tr>
     <td><b>1949-1953</b></td>
     <td><a href="057_pra6.html#truman">Harry S. Truman</a></td>
     <td><a href="058_fla4.html#truman">Bess Wallace Truman</a></td>
     <td><a href="059_vpa1.html#barkley">Barkley, Alben W.</a></td>
     </tr>
     <tr>
     <td><b>1953-1961</b></td>
     <td><a href="057_pra2.html#eisenhower">Dwight D. Eisenhower</a></td>
     <td><a href="058_fla2.html#eisenhower">Mamie Doud Eisenhower</a></td>
     <td><a href="059_vpa3.html#nixon">Richard M. Nixon</a></td>
     </tr>
     <tr>
     <td><b>1961-1963</b></td>
     <td><a href="057_pra4.html#kennedy">John F. Kennedy</a></td>
     <td><a href="058_fla3.html#kennedy">Jacqueline Kennedy</a></td>
     <td><a href="059_vpa3.html#johnsonl">Lyndon B. Johnson</a></td>
     </tr>
     <tr>
     <td><b>1963-1965</b></td>
     <td><a href="057_pra4.html#johnsonl">Lyndon B. Johnson</a></td>
     <td><a href="058_fla3.html#johnsonl">Lady Bird Johnson</a></td>
     <td>office vacant</td>
     </tr>
     <tr>
     <td><b>1965-1969</b></td>
     <td><a href="057_pra4.html#johnsonl">Lyndon B. Johnson</a></td>
     <td><a href="058_fla3.html#johnsonl">Lady Bird Johnson</a></td>
     <td><a href="059_vpa3.html#humphrey">Hubert H. Humphrey</a></td>
     </tr>
     <tr>
     <td><b>1969-1973</b></td>
     <td><a href="057_pra5.html#nixon">Richard M. Nixon</a></td>
     <td><a href="058_fla3.html#nixon">Pat Nixon</a></td>
     <td><a href="059_vpa1.html#agnew">Spiro T. Agnew</a></td>
     </tr>
     <tr>
     <td><b>1973-1974</b></td>
     <td><a href="057_pra5.html#nixon">Richard M. Nixon</a></td>
     <td><a href="058_fla3.html#nixon">Pat Nixon</a></td>
     <td><a href="059_vpa2.html#ford">Gerald R. Ford</a></td>
     </tr>
     <tr>
     <td><b>1974-1977</b></td>
     <td><a href="057_pra2.html#ford">Gerald R. Ford</a></td>
     <td><a href="058_fla2.html#ford">Betty Ford</a></td>
     <td><a href="059_vpa3.html#rockefeller">Nelson Rockefeller</a></td>
     </tr>
     <tr>
     <td><b>1977-1981</b></td>
     <td><a href="057_pra1.html#carter">Jimmy Carter</a></td>
     <td><a href="058_fla1.html#carter">Rosalynn Carter</a></td>
     <td><a href="059_vpa3.html#mondale">Walter F. Mondale</a></td>
     </tr>
     <tr>
     <td><b>1981-1989</b></td>
     <td><a href="057_pra5.html#reagan">Ronald Reagan</a></td>
     <td><a href="058_fla4.html#reagan">Nancy Reagan</a></td>
     <td><a href="059_vpa1.html#bush">George Bush</a></td>
     </tr>
     <tr>
     <td><b>1989-1993</b></td>
     <td><a href="057_pra1.html#bush">George Bush</a></td>
     <td><a href="058_fla1.html#bush">Barbara Bush</a></td>
     <td><a href="059_vpa3.html#quayle">Dan Quayle</a></td>
     </tr>
     <tr>
     <td><b>1993-2001</b></td>
     <td><a href="057_pra2.html#clinton">Bill Clinton</a></td>
     <td><a href="058_fla1.html#clinton">Hillary Rodham Clinton</a></td>
     <td><a href="059_vpa2.html#gore">Albert Gore</a></td>
     </tr>
     <tr>
     <td><b>2001-2009</b></td>
     <td><a href="057_pra1.html#bushgw">George W. Bush</a></td>
     <td><a href="058_fla1.html#bushl">Laura Bush</a></td>
     <td><a href="../info/gwbushinfo.html">Richard Cheney</a></td>
     </tr>
     <tr>
     <td><b>2009-2017</b></td>
     <td><a href="057_pra5.html#obama">Barack Obama</a></td>
     <td><a href="058_fla3.html#obama">Michelle Obama</a></td>
     <td><a href="059_vpa1.html#biden">Joseph R. Biden</a></td>
     </tr>
     <tr>
     <td><b>2017-2021</b></td>
     <td><a href="057_pra6.html#trump">Donald J. Trump</a></td>
     <td><a href="058_fla4.html#trump">Melania Trump</a></td>
     <td><a href="059_vpa3.html#pence">Mike Pence</a></td>
     </tr>
     <tr>
     <td><b>2021-</b></td>
     <td><a href="057_pra1.html#biden">Joseph R. Biden</a></td>
     <td><a href="058_fla1.html#biden">Jill Biden</a></td>
     <td><a href="059_vpa2.html#harris">Kamala Harris</a></td>
     </tr>
     </table>
     <p>
     <!-- #BeginLibraryItem "/Library/pres-menu.lbi" -->
     <table bgcolor="#eeeeee" border="0" cellpadding="5" cellspacing="0" width="100%">
     <tr align="center">
     <td><strong>Presidents:</strong> <a href="057_intr.html">Introduction (Rights/Ordering
           Info.)</a> | <a href="057_pra1.html">Adams
             - Cleveland</a> | <a href="057_pra2.html">Clinton - Harding</a> <br/>
     <a href="057_pra3.html">Harrison
             - Jefferson</a> | <a href="057_pra4.html">Johnson - McKinley</a> | <a href="057_pra5.html">Monroe
               - Roosevelt</a> | <a href="057_pra6.html">Taft - Trump</a> | <a href="057_pra7.html">Tyler
                 - Wilson</a><br/>
     <a href="057_pral.html">List of names, Alphabetically</a> | <a href="057_chron.html">List
             of names, Chronologically</a></td>
     </tr>
     </table>
     <!-- #EndLibraryItem --><!-- #BeginLibraryItem "/Library/fla-menu.lbi" -->
     <table bgcolor="#eeeeee" border="0" cellpadding="8" cellspacing="0" width="100%">
     <tr align="center">
     <td><strong>First Ladies</strong>: <a href="058_intr.html">Introduction
           (Rights/Ordering Info.)</a> | <a href="058_fla1.html">Adams
             - Coolidge</a> | <a href="058_fla2.html">Eisenhower - Hoover<br/>
     </a><a href="058_fla3.html">Jackson
                 - Pierce</a> | <a href="058_fla3.html"></a> <a href="058_fla4.html">Polk - Wilson</a> | <a href="058_flal.html">List
                   of names, Alphabetically</a></td>
     </tr>
     </table>
     <!-- #EndLibraryItem -->
     <!-- #BeginLibraryItem "/Library/vicepres-menu.lbi" -->
     <table bgcolor="#eeeeee" border="0" cellpadding="5" cellspacing="0" width="100%">
     <tr align="center">
     <td> <strong>Vice Presidents:</strong> <a href="059_vp_intr.html">Introduction (Rights/Ordering Info.)</a> | <a href="059_vpa1.html">Adams - Coolidge</a> | <a href="059_vpa2.html">Curtis - Hobart</a> <br/>
     <a href="059_vpa3.html">Humphrey - Rockefeller</a> | <a href="059_vpa4.html">Roosevelt - Wilson</a><br/>
     <a href="059_vp_alpha.html">List of names, Alphabetically</a> | <a href="057_chron.html">List of names, Chronologically</a></td>
     </tr>
     </table>
     <!-- #EndLibraryItem --><!-- #EndLibraryItem --><!-- InstanceEndEditable --></p></p></td>
     </tr>
     <tr valign="top">
     <td><a href="#top"><img align="left" alt="Top of Page" border="0" height="22" src="../images/up-button.gif" width="22"/></a> <a href="#top">Top
                   of Page</a> </td>
     </tr>
     </table>
     <!-- end content table -->
     </td>
     </tr>,
     <tr valign="top">
     <td width="100%"> <!-- InstanceBeginEditable name="content" -->
     <h1>Chronological List of Presidents, First Ladies, and Vice Presidents of the United States</h1>
     <h2>Selected Images From the Collections of the Library of Congress</h2>
     <p><strong><a href="//www.loc.gov/rr/print/pphome.html">Prints and Photographs Division</a>, Library of
                   Congress, Washington, D.C., 20540-4730</strong>
     </p>
     <p>
     This chronological list contains entries for each president with his corresponding first lady and vice president. Note: Multiple entries appear for a president whenever there was a change in the office of vice president.
     </p>
     <p>
     <table border="1" cellpadding="4" cellspacing="2">
     <tr>
     <th width="55">YEAR</th>
     <th width="124">PRESIDENT</th>
     <th width="266">FIRST LADY</th>
     <th width="159">VICE PRESIDENT</th>
     </tr>
     <tr>
     <td><b>1789-1797</b></td>
     <td><a href="057_pra7.html#washington">George Washington</a></td>
     <td><a href="058_fla4.html#washington">Martha Washington</a></td>
     <td><a href="059_vpa1.html#adamsj">John Adams</a></td>
     </tr>
     <tr>
     <td><b>1797-1801</b></td>
     <td><a href="057_pra1.html#adamsj">John Adams</a></td>
     <td><a href="058_fla1.html#adamsa">Abigail Adams</a></td>
     <td><a href="059_vpa3.html#jefferson">Thomas Jefferson</a></td>
     </tr>
     <tr>
     <td><b>1801-1805</b></td>
     <td><a href="057_pra3.html#jefferson">Thomas Jefferson</a></td>
     <td><p>[Martha Wayles Skelton Jefferson <br/>
         died before Jefferson assumed office;<br/>
     no image of her in P&amp;P collections]</p></td>
     <td><a href="059_vpa1.html#burr">Aaron Burr</a></td>
     </tr>
     <tr>
     <td><b>1805-1809</b></td>
     <td><a href="057_pra3.html#jefferson">Thomas Jefferson</a></td>
     <td>see above</td>
     <td><a href="059_vpa1.html#clinton">George Clinton</a></td>
     </tr>
     <tr>
     <td><b>1809-1812</b></td>
     <td><a href="057_pra4.html#madison">James Madison</a></td>
     <td><a href="058_fla3.html#madison">Dolley Madison</a></td>
     <td><a href="059_vpa1.html#clinton">George Clinton</a></td>
     </tr>
     <tr>
     <td><b>1812-1813</b></td>
     <td><a href="057_pra4.html#madison">James Madison</a></td>
     <td><a href="058_fla3.html#madison">Dolley Madison</a></td>
     <td>office vacant</td>
     </tr>
     <tr>
     <td><b>1813-1814</b></td>
     <td><a href="057_pra4.html#madison">James Madison</a></td>
     <td><a href="058_fla3.html#madison">Dolley Madison</a></td>
     <td><a href="059_vpa2.html#gerry">Elbridge Gerry</a></td>
     </tr>
     <tr>
     <td><b>1814-1817</b></td>
     <td><a href="057_pra5.html#madison">James Madison</a></td>
     <td><a href="058_fla3.html#madison">Dolley Madison</a></td>
     <td>office vacant</td>
     </tr>
     <tr>
     <td><b>1817-1825</b></td>
     <td><a href="057_pra5.html#monroe">James Monroe</a></td>
     <td>Elizabeth Kortright Monroe<br/>
        (no image)</td>
     <td><a href="059_vpa4.html#tompkins">Daniel D. Tompkins</a></td>
     </tr>
     <tr>
     <td><b>1825-1829</b></td>
     <td><a href="057_pra1.html#adamsjq">John Quincy Adams</a></td>
     <td><a href="058_fla1.html#adamsl">Louisa Catherine Adams</a></td>
     <td><a href="059_vpa1.html#calhoun">John C. Calhoun</a></td>
     </tr>
     <tr>
     <td><b>1829-1832</b></td>
     <td><a href="057_pra3.html#jackson">Andrew Jackson</a></td>
     <td><a href="058_fla3.html#jackson">Rachel Jackson</a> [Rachel Donelson Jackson 
     died before Jackson assumed office and did not serve as first lady]</td>
     <td><a href="059_vpa1.html#calhoun">John C. Calhoun</a></td>
     </tr>
     <tr>
     <td><b>1833-1837</b></td>
     <td><a href="057_pra3.html#jackson">Andrew Jackson</a></td>
     <td><a href="058_fla3.html#jackson">Rachel Jackson</a> [Rachel Donelson Jackson 
     died before Jackson assumed office and did not serve as first lady]</td>
     <td><a href="059_vpa4.html#vanburen">Martin Van Buren</a></td>
     </tr>
     <tr>
     <td><b>1837-1841</b></td>
     <td><a href="057_pra7.html#vanburen">Martin Van Buren</a></td>
     <td><a href="058_fla4.html#vanburen">Hannah Hoes Van Buren</a></td>
     <td><a href="059_vpa3.html#johnsonr">Richard M. Johnson</a></td>
     </tr>
     <tr>
     <td><b>1841</b></td>
     <td><a href="057_pra3.html#harrisonw">William Henry Harrison</a></td>
     <td><a href="058_fla2.html#harrisona">Anna Tuthill Symmes Harrison</a></td>
     <td><a href="059_vpa4.html#tyler">John Tyler</a></td>
     </tr>
     <tr>
     <td><b>1841-1845</b></td>
     <td><a href="057_pra7.html#tyler">John Tyler</a></td>
     <td>Letitia Christian Tyler and<br/> Julia Gardiner Tyler (no images)</td>
     <td>office vacant</td>
     </tr>
     <tr>
     <td><b>1845-1849</b></td>
     <td><a href="057_pra5.html#polk">James K. Polk</a></td>
     <td><a href="058_fla4.html#polk">Sarah Childress Polk</a></td>
     <td><a href="059_vpa2.html#dallas">George M. Dallas</a></td>
     </tr>
     <tr>
     <td><b>1849-1850</b></td>
     <td><a href="057_pra6.html#taylor">Zachary Taylor</a></td>
     <td>Margaret Mackall Smith Taylor<br/>
        (no image)</td>
     <td><a href="059_vpa2.html#fillmore">Millard Fillmore</a></td>
     </tr>
     <tr>
     <td><b>1850-1853</b></td>
     <td><a href="057_pra2.html#fillmore">Millard Fillmore</a></td>
     <td><a href="058_fla2.html#fillmore">Abigail Powers Fillmore</a></td>
     <td>office vacant</td>
     </tr>
     <tr>
     <td><b>1853</b></td>
     <td><a href="057_pra5.html#pierce">Franklin Pierce</a></td>
     <td><a href="058_fla4.html#pierce">Jane M. Pierce</a></td>
     <td><a href="059_vpa3.html#king">William R. King</a></td>
     </tr>
     <tr>
     <td><b>1853-1857</b></td>
     <td><a href="057_pra5.html#pierce">Franklin Pierce</a></td>
     <td><a href="058_fla4.html#pierce">Jane M. Pierce</a></td>
     <td>office vacant</td>
     </tr>
     <tr>
     <td><b>1857-1861</b></td>
     <td><a href="057_pra1.html#buchanan">James Buchanan</a></td>
     <td>(never married)</td>
     <td><a href="059_vpa1.html#breck">John C. Breckinridge</a></td>
     </tr>
     <tr>
     <td><b>1861-1865</b></td>
     <td><a href="057_pra4.html#lincoln">Abraham Lincoln</a></td>
     <td><a href="058_fla3.html#lincoln">Mary Todd Lincoln</a></td>
     <td><a href="059_vpa2.html#hamlin">Hannibal Hamlin</a></td>
     </tr>
     <tr>
     <td><b>1865</b></td>
     <td><a href="057_pra4.html#lincoln">Abraham Lincoln</a></td>
     <td><a href="058_fla3.html#lincoln">Mary Todd Lincoln</a></td>
     <td><a href="059_vpa3.html#johnsona">Andrew Johnson</a></td>
     </tr>
     <tr>
     <td><b>1865-1869</b></td>
     <td><a href="057_pra4.html#johnsona">Andrew Johnson</a></td>
     <td><a href="058_fla3.html#johnsone">Eliza McCardle Johnson</a></td>
     <td>office vacant</td>
     </tr>
     <tr>
     <td><b>1869-1873</b></td>
     <td><a href="057_pra2.html#grant">Ulysses S. Grant</a></td>
     <td><a href="058_fla2.html#grant">Julia Dent Grant</a></td>
     <td><a href="059_vpa1.html#colfax">Schuyler Colfax</a></td>
     </tr>
     <tr>
     <td><b>1873-1875</b></td>
     <td><a href="057_pra2.html#grant">Ulysses S. Grant</a></td>
     <td><a href="058_fla2.html#grant">Julia Dent Grant</a></td>
     <td><a href="059_vpa4.html#wilson">Henry Wilson</a></td>
     </tr>
     <tr>
     <td><b>1875-1877</b></td>
     <td><a href="057_pra2.html#grant">Ulysses S. Grant</a></td>
     <td><a href="058_fla2.html#grant">Julia Dent Grant</a></td>
     <td>office vacant</td>
     </tr>
     <tr>
     <td><b>1877-1881</b></td>
     <td><a href="057_pra3.html#hayes">Rutherford Birchard Hayes</a></td>
     <td><a href="058_fla2.html#hayes">Lucy Webb Hayes</a></td>
     <td><a href="059_vpa4.html#wheeler">William A. Wheeler</a></td>
     </tr>
     <tr>
     <td><b>1881</b></td>
     <td><a href="057_pra2.html#garfield">James A. Garfield</a></td>
     <td><a href="058_fla2.html#garfield">Lucretia Rudolph Garfield</a></td>
     <td><a href="059_vpa1.html#arthur">Chester A. Arthur</a></td>
     </tr>
     <tr>
     <td><b>1881-1885</b></td>
     <td><a href="057_pra1.html#arthur">Chester A. Arthur</a></td>
     <td><a href="058_fla1.html#arthur">Ellen Lewis Herndon Arthur</a></td>
     <td>office vacant</td>
     </tr>
     <tr>
     <td><b>1885</b></td>
     <td><a href="057_pra1.html#cleveland">Grover Cleveland</a></td>
     <td><a href="058_fla1.html#cleveland">Frances Folsom Cleveland</a></td>
     <td><a href="059_vpa2.html#hendricks">Thomas A. Hendricks</a></td>
     </tr>
     <tr>
     <td><b>1885-1889</b></td>
     <td><a href="057_pra1.html#cleveland">Grover Cleveland</a></td>
     <td><a href="058_fla1.html#cleveland">Frances Folsom Cleveland</a></td>
     <td>office vacant</td>
     </tr>
     <tr>
     <td><b>1889-1893</b></td>
     <td><a href="057_pra3.html#harrisonb">Benjamin Harrison</a></td>
     <td><a href="058_fla2.html#harrisonc">Caroline Lavinia Scott Harrison</a><br/>
     <a href="058_fla2.html#harrisonm">Mary Lord Harrison</a><br/>
        [Harrison's second wife,<br/>
         but never a first lady]</td>
     <td><a href="059_vpa3.html#morton">Levi P. Morton</a></td>
     </tr>
     <tr>
     <td><b>1893-1897</b></td>
     <td><a href="057_pra1.html#cleveland">Grover Cleveland</a></td>
     <td><a href="058_fla1.html#cleveland">Frances Folsom Cleveland</a></td>
     <td><a href="059_vpa4.html#stevenson">Adlai E. Stevenson</a></td>
     </tr>
     <tr>
     <td><b>1897-1899</b></td>
     <td><a href="057_pra4.html#mckinley">William McKinley</a></td>
     <td><a href="058_fla3.html#mckinley">Ida Saxton McKinley</a></td>
     <td><a href="059_vpa2.html#hobart">Garret A. Hobart</a></td>
     </tr>
     <tr>
     <td><b>1899-1901</b></td>
     <td><a href="057_pra4.html#mckinley">William McKinley</a></td>
     <td><a href="058_fla3.html#mckinley">Ida Saxton McKinley</a></td>
     <td>office vacant</td>
     </tr>
     <tr>
     <td><b>1901</b></td>
     <td><a href="057_pra4.html#mckinley">William McKinley</a></td>
     <td><a href="058_fla3.html#mckinley">Ida Saxton McKinley</a></td>
     <td><a href="059_vpa4.html#roosevelt">Theodore Roosevelt</a></td>
     </tr>
     <tr>
     <td><b>1901-1905</b></td>
     <td><a href="057_pra5.html#rooseveltt">Theodore Roosevelt</a></td>
     <td><a href="058_fla4.html#roosevelted">Edith Kermit Carow Roosevelt</a></td>
     <td>office vacant</td>
     </tr>
     <tr>
     <td><b>1905-1909</b></td>
     <td><a href="057_pra5.html#rooseveltt">Theodore Roosevelt</a></td>
     <td><a href="058_fla4.html#roosevelted">Edith Kermit Carow Roosevelt</a></td>
     <td><a href="059_vpa2.html#fairbanks">Charles W. Fairbanks</a></td>
     </tr>
     <tr>
     <td><b>1909-1912</b></td>
     <td><a href="057_pra6.html#taft">William H. Taft</a></td>
     <td><a href="058_fla4.html#taft">Helen Herron Taft</a></td>
     <td><a href="059_vpa4.html#sherman">James S. Sherman</a></td>
     </tr>
     <tr>
     <td><b>1912-1913</b></td>
     <td><a href="057_pra6.html#taft">William H. Taft</a></td>
     <td><a href="058_fla4.html#taft">Helen Herron Taft</a></td>
     <td>office vacant</td>
     </tr>
     <tr>
     <td><b>1913-1921</b></td>
     <td><a href="057_pra7.html#wilson">Woodrow Wilson</a></td>
     <td><a href="058_fla4.html#wilsonel">Ellen Axson Wilson</a> and <br/>
     <a href="058_fla4.html#wilsoned">Edith
           Bolling Galt Wilson</a></td>
     <td><a href="059_vpa3.html#marshall">Thomas R. Marshall</a></td>
     </tr>
     <tr>
     <td><b>1921-1923</b></td>
     <td><a href="057_pra2.html#harding">Warren G. Harding</a></td>
     <td><a href="058_fla2.html#harding">Florence Kling Harding</a></td>
     <td><a href="059_vpa1.html#coolidge">Calvin Coolidge</a></td>
     </tr>
     <tr>
     <td><b>1923-1925</b></td>
     <td><a href="057_pra2.html#coolidge">Calvin Coolidge</a></td>
     <td><a href="058_fla1.html#coolidge">Grace Goodhue Coolidge</a></td>
     <td>office vacant</td>
     </tr>
     <tr>
     <td><b>1925-1929</b></td>
     <td><a href="057_pra2.html#coolidge">Calvin Coolidge</a></td>
     <td><a href="058_fla1.html#coolidge">Grace Goodhue Coolidge</a></td>
     <td><a href="059_vpa2.html#dawes">Charles G. Dawes</a></td>
     </tr>
     <tr>
     <td><b>1929-1933</b></td>
     <td><a href="057_pra3.html#hoover">Herbert Hoover</a></td>
     <td><a href="058_fla3.html#hoover">Lou Henry Hoover</a></td>
     <td><a href="059_vpa2.html#curtis">Charles Curtis</a></td>
     </tr>
     <tr>
     <td><b>1933-1941</b></td>
     <td><a href="057_pra5.html#rooseveltf">Franklin D. Roosevelt</a></td>
     <td><a href="058_fla4.html#rooseveltel">Eleanor Roosevelt</a></td>
     <td><a href="059_vpa2.html#garner">John N. Garner</a></td>
     </tr>
     <tr>
     <td><b>1941-1945</b></td>
     <td><a href="057_pra5.html#rooseveltf">Franklin D. Roosevelt</a></td>
     <td><a href="058_fla4.html#rooseveltel">Eleanor Roosevelt</a></td>
     <td><a href="059_vpa4.html#wallace">Henry A. Wallace</a></td>
     </tr>
     <tr>
     <td><b>1945</b></td>
     <td><a href="057_pra5.html#rooseveltf">Franklin D. Roosevelt</a></td>
     <td><a href="058_fla4.html#rooseveltel">Eleanor Roosevelt</a></td>
     <td><a href="059_vpa4.html#truman">Harry S. Truman</a></td>
     </tr>
     <tr>
     <td><b>1945-1949</b></td>
     <td><a href="057_pra6.html#truman">Harry S. Truman</a></td>
     <td><a href="058_fla4.html#truman">Bess Wallace Truman</a></td>
     <td>office vacant</td>
     </tr>
     <tr>
     <td><b>1949-1953</b></td>
     <td><a href="057_pra6.html#truman">Harry S. Truman</a></td>
     <td><a href="058_fla4.html#truman">Bess Wallace Truman</a></td>
     <td><a href="059_vpa1.html#barkley">Barkley, Alben W.</a></td>
     </tr>
     <tr>
     <td><b>1953-1961</b></td>
     <td><a href="057_pra2.html#eisenhower">Dwight D. Eisenhower</a></td>
     <td><a href="058_fla2.html#eisenhower">Mamie Doud Eisenhower</a></td>
     <td><a href="059_vpa3.html#nixon">Richard M. Nixon</a></td>
     </tr>
     <tr>
     <td><b>1961-1963</b></td>
     <td><a href="057_pra4.html#kennedy">John F. Kennedy</a></td>
     <td><a href="058_fla3.html#kennedy">Jacqueline Kennedy</a></td>
     <td><a href="059_vpa3.html#johnsonl">Lyndon B. Johnson</a></td>
     </tr>
     <tr>
     <td><b>1963-1965</b></td>
     <td><a href="057_pra4.html#johnsonl">Lyndon B. Johnson</a></td>
     <td><a href="058_fla3.html#johnsonl">Lady Bird Johnson</a></td>
     <td>office vacant</td>
     </tr>
     <tr>
     <td><b>1965-1969</b></td>
     <td><a href="057_pra4.html#johnsonl">Lyndon B. Johnson</a></td>
     <td><a href="058_fla3.html#johnsonl">Lady Bird Johnson</a></td>
     <td><a href="059_vpa3.html#humphrey">Hubert H. Humphrey</a></td>
     </tr>
     <tr>
     <td><b>1969-1973</b></td>
     <td><a href="057_pra5.html#nixon">Richard M. Nixon</a></td>
     <td><a href="058_fla3.html#nixon">Pat Nixon</a></td>
     <td><a href="059_vpa1.html#agnew">Spiro T. Agnew</a></td>
     </tr>
     <tr>
     <td><b>1973-1974</b></td>
     <td><a href="057_pra5.html#nixon">Richard M. Nixon</a></td>
     <td><a href="058_fla3.html#nixon">Pat Nixon</a></td>
     <td><a href="059_vpa2.html#ford">Gerald R. Ford</a></td>
     </tr>
     <tr>
     <td><b>1974-1977</b></td>
     <td><a href="057_pra2.html#ford">Gerald R. Ford</a></td>
     <td><a href="058_fla2.html#ford">Betty Ford</a></td>
     <td><a href="059_vpa3.html#rockefeller">Nelson Rockefeller</a></td>
     </tr>
     <tr>
     <td><b>1977-1981</b></td>
     <td><a href="057_pra1.html#carter">Jimmy Carter</a></td>
     <td><a href="058_fla1.html#carter">Rosalynn Carter</a></td>
     <td><a href="059_vpa3.html#mondale">Walter F. Mondale</a></td>
     </tr>
     <tr>
     <td><b>1981-1989</b></td>
     <td><a href="057_pra5.html#reagan">Ronald Reagan</a></td>
     <td><a href="058_fla4.html#reagan">Nancy Reagan</a></td>
     <td><a href="059_vpa1.html#bush">George Bush</a></td>
     </tr>
     <tr>
     <td><b>1989-1993</b></td>
     <td><a href="057_pra1.html#bush">George Bush</a></td>
     <td><a href="058_fla1.html#bush">Barbara Bush</a></td>
     <td><a href="059_vpa3.html#quayle">Dan Quayle</a></td>
     </tr>
     <tr>
     <td><b>1993-2001</b></td>
     <td><a href="057_pra2.html#clinton">Bill Clinton</a></td>
     <td><a href="058_fla1.html#clinton">Hillary Rodham Clinton</a></td>
     <td><a href="059_vpa2.html#gore">Albert Gore</a></td>
     </tr>
     <tr>
     <td><b>2001-2009</b></td>
     <td><a href="057_pra1.html#bushgw">George W. Bush</a></td>
     <td><a href="058_fla1.html#bushl">Laura Bush</a></td>
     <td><a href="../info/gwbushinfo.html">Richard Cheney</a></td>
     </tr>
     <tr>
     <td><b>2009-2017</b></td>
     <td><a href="057_pra5.html#obama">Barack Obama</a></td>
     <td><a href="058_fla3.html#obama">Michelle Obama</a></td>
     <td><a href="059_vpa1.html#biden">Joseph R. Biden</a></td>
     </tr>
     <tr>
     <td><b>2017-2021</b></td>
     <td><a href="057_pra6.html#trump">Donald J. Trump</a></td>
     <td><a href="058_fla4.html#trump">Melania Trump</a></td>
     <td><a href="059_vpa3.html#pence">Mike Pence</a></td>
     </tr>
     <tr>
     <td><b>2021-</b></td>
     <td><a href="057_pra1.html#biden">Joseph R. Biden</a></td>
     <td><a href="058_fla1.html#biden">Jill Biden</a></td>
     <td><a href="059_vpa2.html#harris">Kamala Harris</a></td>
     </tr>
     </table>
     <p>
     <!-- #BeginLibraryItem "/Library/pres-menu.lbi" -->
     <table bgcolor="#eeeeee" border="0" cellpadding="5" cellspacing="0" width="100%">
     <tr align="center">
     <td><strong>Presidents:</strong> <a href="057_intr.html">Introduction (Rights/Ordering
           Info.)</a> | <a href="057_pra1.html">Adams
             - Cleveland</a> | <a href="057_pra2.html">Clinton - Harding</a> <br/>
     <a href="057_pra3.html">Harrison
             - Jefferson</a> | <a href="057_pra4.html">Johnson - McKinley</a> | <a href="057_pra5.html">Monroe
               - Roosevelt</a> | <a href="057_pra6.html">Taft - Trump</a> | <a href="057_pra7.html">Tyler
                 - Wilson</a><br/>
     <a href="057_pral.html">List of names, Alphabetically</a> | <a href="057_chron.html">List
             of names, Chronologically</a></td>
     </tr>
     </table>
     <!-- #EndLibraryItem --><!-- #BeginLibraryItem "/Library/fla-menu.lbi" -->
     <table bgcolor="#eeeeee" border="0" cellpadding="8" cellspacing="0" width="100%">
     <tr align="center">
     <td><strong>First Ladies</strong>: <a href="058_intr.html">Introduction
           (Rights/Ordering Info.)</a> | <a href="058_fla1.html">Adams
             - Coolidge</a> | <a href="058_fla2.html">Eisenhower - Hoover<br/>
     </a><a href="058_fla3.html">Jackson
                 - Pierce</a> | <a href="058_fla3.html"></a> <a href="058_fla4.html">Polk - Wilson</a> | <a href="058_flal.html">List
                   of names, Alphabetically</a></td>
     </tr>
     </table>
     <!-- #EndLibraryItem -->
     <!-- #BeginLibraryItem "/Library/vicepres-menu.lbi" -->
     <table bgcolor="#eeeeee" border="0" cellpadding="5" cellspacing="0" width="100%">
     <tr align="center">
     <td> <strong>Vice Presidents:</strong> <a href="059_vp_intr.html">Introduction (Rights/Ordering Info.)</a> | <a href="059_vpa1.html">Adams - Coolidge</a> | <a href="059_vpa2.html">Curtis - Hobart</a> <br/>
     <a href="059_vpa3.html">Humphrey - Rockefeller</a> | <a href="059_vpa4.html">Roosevelt - Wilson</a><br/>
     <a href="059_vp_alpha.html">List of names, Alphabetically</a> | <a href="057_chron.html">List of names, Chronologically</a></td>
     </tr>
     </table>
     <!-- #EndLibraryItem --><!-- #EndLibraryItem --><!-- InstanceEndEditable --></p></p></td>
     </tr>,
     <tr>
     <th width="55">YEAR</th>
     <th width="124">PRESIDENT</th>
     <th width="266">FIRST LADY</th>
     <th width="159">VICE PRESIDENT</th>
     </tr>,
     <tr>
     <td><b>1789-1797</b></td>
     <td><a href="057_pra7.html#washington">George Washington</a></td>
     <td><a href="058_fla4.html#washington">Martha Washington</a></td>
     <td><a href="059_vpa1.html#adamsj">John Adams</a></td>
     </tr>,
     <tr>
     <td><b>1797-1801</b></td>
     <td><a href="057_pra1.html#adamsj">John Adams</a></td>
     <td><a href="058_fla1.html#adamsa">Abigail Adams</a></td>
     <td><a href="059_vpa3.html#jefferson">Thomas Jefferson</a></td>
     </tr>,
     <tr>
     <td><b>1801-1805</b></td>
     <td><a href="057_pra3.html#jefferson">Thomas Jefferson</a></td>
     <td><p>[Martha Wayles Skelton Jefferson <br/>
         died before Jefferson assumed office;<br/>
     no image of her in P&amp;P collections]</p></td>
     <td><a href="059_vpa1.html#burr">Aaron Burr</a></td>
     </tr>,
     <tr>
     <td><b>1805-1809</b></td>
     <td><a href="057_pra3.html#jefferson">Thomas Jefferson</a></td>
     <td>see above</td>
     <td><a href="059_vpa1.html#clinton">George Clinton</a></td>
     </tr>,
     <tr>
     <td><b>1809-1812</b></td>
     <td><a href="057_pra4.html#madison">James Madison</a></td>
     <td><a href="058_fla3.html#madison">Dolley Madison</a></td>
     <td><a href="059_vpa1.html#clinton">George Clinton</a></td>
     </tr>,
     <tr>
     <td><b>1812-1813</b></td>
     <td><a href="057_pra4.html#madison">James Madison</a></td>
     <td><a href="058_fla3.html#madison">Dolley Madison</a></td>
     <td>office vacant</td>
     </tr>,
     <tr>
     <td><b>1813-1814</b></td>
     <td><a href="057_pra4.html#madison">James Madison</a></td>
     <td><a href="058_fla3.html#madison">Dolley Madison</a></td>
     <td><a href="059_vpa2.html#gerry">Elbridge Gerry</a></td>
     </tr>,
     <tr>
     <td><b>1814-1817</b></td>
     <td><a href="057_pra5.html#madison">James Madison</a></td>
     <td><a href="058_fla3.html#madison">Dolley Madison</a></td>
     <td>office vacant</td>
     </tr>,
     <tr>
     <td><b>1817-1825</b></td>
     <td><a href="057_pra5.html#monroe">James Monroe</a></td>
     <td>Elizabeth Kortright Monroe<br/>
        (no image)</td>
     <td><a href="059_vpa4.html#tompkins">Daniel D. Tompkins</a></td>
     </tr>,
     <tr>
     <td><b>1825-1829</b></td>
     <td><a href="057_pra1.html#adamsjq">John Quincy Adams</a></td>
     <td><a href="058_fla1.html#adamsl">Louisa Catherine Adams</a></td>
     <td><a href="059_vpa1.html#calhoun">John C. Calhoun</a></td>
     </tr>,
     <tr>
     <td><b>1829-1832</b></td>
     <td><a href="057_pra3.html#jackson">Andrew Jackson</a></td>
     <td><a href="058_fla3.html#jackson">Rachel Jackson</a> [Rachel Donelson Jackson 
     died before Jackson assumed office and did not serve as first lady]</td>
     <td><a href="059_vpa1.html#calhoun">John C. Calhoun</a></td>
     </tr>,
     <tr>
     <td><b>1833-1837</b></td>
     <td><a href="057_pra3.html#jackson">Andrew Jackson</a></td>
     <td><a href="058_fla3.html#jackson">Rachel Jackson</a> [Rachel Donelson Jackson 
     died before Jackson assumed office and did not serve as first lady]</td>
     <td><a href="059_vpa4.html#vanburen">Martin Van Buren</a></td>
     </tr>,
     <tr>
     <td><b>1837-1841</b></td>
     <td><a href="057_pra7.html#vanburen">Martin Van Buren</a></td>
     <td><a href="058_fla4.html#vanburen">Hannah Hoes Van Buren</a></td>
     <td><a href="059_vpa3.html#johnsonr">Richard M. Johnson</a></td>
     </tr>,
     <tr>
     <td><b>1841</b></td>
     <td><a href="057_pra3.html#harrisonw">William Henry Harrison</a></td>
     <td><a href="058_fla2.html#harrisona">Anna Tuthill Symmes Harrison</a></td>
     <td><a href="059_vpa4.html#tyler">John Tyler</a></td>
     </tr>,
     <tr>
     <td><b>1841-1845</b></td>
     <td><a href="057_pra7.html#tyler">John Tyler</a></td>
     <td>Letitia Christian Tyler and<br/> Julia Gardiner Tyler (no images)</td>
     <td>office vacant</td>
     </tr>,
     <tr>
     <td><b>1845-1849</b></td>
     <td><a href="057_pra5.html#polk">James K. Polk</a></td>
     <td><a href="058_fla4.html#polk">Sarah Childress Polk</a></td>
     <td><a href="059_vpa2.html#dallas">George M. Dallas</a></td>
     </tr>,
     <tr>
     <td><b>1849-1850</b></td>
     <td><a href="057_pra6.html#taylor">Zachary Taylor</a></td>
     <td>Margaret Mackall Smith Taylor<br/>
        (no image)</td>
     <td><a href="059_vpa2.html#fillmore">Millard Fillmore</a></td>
     </tr>,
     <tr>
     <td><b>1850-1853</b></td>
     <td><a href="057_pra2.html#fillmore">Millard Fillmore</a></td>
     <td><a href="058_fla2.html#fillmore">Abigail Powers Fillmore</a></td>
     <td>office vacant</td>
     </tr>,
     <tr>
     <td><b>1853</b></td>
     <td><a href="057_pra5.html#pierce">Franklin Pierce</a></td>
     <td><a href="058_fla4.html#pierce">Jane M. Pierce</a></td>
     <td><a href="059_vpa3.html#king">William R. King</a></td>
     </tr>,
     <tr>
     <td><b>1853-1857</b></td>
     <td><a href="057_pra5.html#pierce">Franklin Pierce</a></td>
     <td><a href="058_fla4.html#pierce">Jane M. Pierce</a></td>
     <td>office vacant</td>
     </tr>,
     <tr>
     <td><b>1857-1861</b></td>
     <td><a href="057_pra1.html#buchanan">James Buchanan</a></td>
     <td>(never married)</td>
     <td><a href="059_vpa1.html#breck">John C. Breckinridge</a></td>
     </tr>,
     <tr>
     <td><b>1861-1865</b></td>
     <td><a href="057_pra4.html#lincoln">Abraham Lincoln</a></td>
     <td><a href="058_fla3.html#lincoln">Mary Todd Lincoln</a></td>
     <td><a href="059_vpa2.html#hamlin">Hannibal Hamlin</a></td>
     </tr>,
     <tr>
     <td><b>1865</b></td>
     <td><a href="057_pra4.html#lincoln">Abraham Lincoln</a></td>
     <td><a href="058_fla3.html#lincoln">Mary Todd Lincoln</a></td>
     <td><a href="059_vpa3.html#johnsona">Andrew Johnson</a></td>
     </tr>,
     <tr>
     <td><b>1865-1869</b></td>
     <td><a href="057_pra4.html#johnsona">Andrew Johnson</a></td>
     <td><a href="058_fla3.html#johnsone">Eliza McCardle Johnson</a></td>
     <td>office vacant</td>
     </tr>,
     <tr>
     <td><b>1869-1873</b></td>
     <td><a href="057_pra2.html#grant">Ulysses S. Grant</a></td>
     <td><a href="058_fla2.html#grant">Julia Dent Grant</a></td>
     <td><a href="059_vpa1.html#colfax">Schuyler Colfax</a></td>
     </tr>,
     <tr>
     <td><b>1873-1875</b></td>
     <td><a href="057_pra2.html#grant">Ulysses S. Grant</a></td>
     <td><a href="058_fla2.html#grant">Julia Dent Grant</a></td>
     <td><a href="059_vpa4.html#wilson">Henry Wilson</a></td>
     </tr>,
     <tr>
     <td><b>1875-1877</b></td>
     <td><a href="057_pra2.html#grant">Ulysses S. Grant</a></td>
     <td><a href="058_fla2.html#grant">Julia Dent Grant</a></td>
     <td>office vacant</td>
     </tr>,
     <tr>
     <td><b>1877-1881</b></td>
     <td><a href="057_pra3.html#hayes">Rutherford Birchard Hayes</a></td>
     <td><a href="058_fla2.html#hayes">Lucy Webb Hayes</a></td>
     <td><a href="059_vpa4.html#wheeler">William A. Wheeler</a></td>
     </tr>,
     <tr>
     <td><b>1881</b></td>
     <td><a href="057_pra2.html#garfield">James A. Garfield</a></td>
     <td><a href="058_fla2.html#garfield">Lucretia Rudolph Garfield</a></td>
     <td><a href="059_vpa1.html#arthur">Chester A. Arthur</a></td>
     </tr>,
     <tr>
     <td><b>1881-1885</b></td>
     <td><a href="057_pra1.html#arthur">Chester A. Arthur</a></td>
     <td><a href="058_fla1.html#arthur">Ellen Lewis Herndon Arthur</a></td>
     <td>office vacant</td>
     </tr>,
     <tr>
     <td><b>1885</b></td>
     <td><a href="057_pra1.html#cleveland">Grover Cleveland</a></td>
     <td><a href="058_fla1.html#cleveland">Frances Folsom Cleveland</a></td>
     <td><a href="059_vpa2.html#hendricks">Thomas A. Hendricks</a></td>
     </tr>,
     <tr>
     <td><b>1885-1889</b></td>
     <td><a href="057_pra1.html#cleveland">Grover Cleveland</a></td>
     <td><a href="058_fla1.html#cleveland">Frances Folsom Cleveland</a></td>
     <td>office vacant</td>
     </tr>,
     <tr>
     <td><b>1889-1893</b></td>
     <td><a href="057_pra3.html#harrisonb">Benjamin Harrison</a></td>
     <td><a href="058_fla2.html#harrisonc">Caroline Lavinia Scott Harrison</a><br/>
     <a href="058_fla2.html#harrisonm">Mary Lord Harrison</a><br/>
        [Harrison's second wife,<br/>
         but never a first lady]</td>
     <td><a href="059_vpa3.html#morton">Levi P. Morton</a></td>
     </tr>,
     <tr>
     <td><b>1893-1897</b></td>
     <td><a href="057_pra1.html#cleveland">Grover Cleveland</a></td>
     <td><a href="058_fla1.html#cleveland">Frances Folsom Cleveland</a></td>
     <td><a href="059_vpa4.html#stevenson">Adlai E. Stevenson</a></td>
     </tr>,
     <tr>
     <td><b>1897-1899</b></td>
     <td><a href="057_pra4.html#mckinley">William McKinley</a></td>
     <td><a href="058_fla3.html#mckinley">Ida Saxton McKinley</a></td>
     <td><a href="059_vpa2.html#hobart">Garret A. Hobart</a></td>
     </tr>,
     <tr>
     <td><b>1899-1901</b></td>
     <td><a href="057_pra4.html#mckinley">William McKinley</a></td>
     <td><a href="058_fla3.html#mckinley">Ida Saxton McKinley</a></td>
     <td>office vacant</td>
     </tr>,
     <tr>
     <td><b>1901</b></td>
     <td><a href="057_pra4.html#mckinley">William McKinley</a></td>
     <td><a href="058_fla3.html#mckinley">Ida Saxton McKinley</a></td>
     <td><a href="059_vpa4.html#roosevelt">Theodore Roosevelt</a></td>
     </tr>,
     <tr>
     <td><b>1901-1905</b></td>
     <td><a href="057_pra5.html#rooseveltt">Theodore Roosevelt</a></td>
     <td><a href="058_fla4.html#roosevelted">Edith Kermit Carow Roosevelt</a></td>
     <td>office vacant</td>
     </tr>,
     <tr>
     <td><b>1905-1909</b></td>
     <td><a href="057_pra5.html#rooseveltt">Theodore Roosevelt</a></td>
     <td><a href="058_fla4.html#roosevelted">Edith Kermit Carow Roosevelt</a></td>
     <td><a href="059_vpa2.html#fairbanks">Charles W. Fairbanks</a></td>
     </tr>,
     <tr>
     <td><b>1909-1912</b></td>
     <td><a href="057_pra6.html#taft">William H. Taft</a></td>
     <td><a href="058_fla4.html#taft">Helen Herron Taft</a></td>
     <td><a href="059_vpa4.html#sherman">James S. Sherman</a></td>
     </tr>,
     <tr>
     <td><b>1912-1913</b></td>
     <td><a href="057_pra6.html#taft">William H. Taft</a></td>
     <td><a href="058_fla4.html#taft">Helen Herron Taft</a></td>
     <td>office vacant</td>
     </tr>,
     <tr>
     <td><b>1913-1921</b></td>
     <td><a href="057_pra7.html#wilson">Woodrow Wilson</a></td>
     <td><a href="058_fla4.html#wilsonel">Ellen Axson Wilson</a> and <br/>
     <a href="058_fla4.html#wilsoned">Edith
           Bolling Galt Wilson</a></td>
     <td><a href="059_vpa3.html#marshall">Thomas R. Marshall</a></td>
     </tr>,
     <tr>
     <td><b>1921-1923</b></td>
     <td><a href="057_pra2.html#harding">Warren G. Harding</a></td>
     <td><a href="058_fla2.html#harding">Florence Kling Harding</a></td>
     <td><a href="059_vpa1.html#coolidge">Calvin Coolidge</a></td>
     </tr>,
     <tr>
     <td><b>1923-1925</b></td>
     <td><a href="057_pra2.html#coolidge">Calvin Coolidge</a></td>
     <td><a href="058_fla1.html#coolidge">Grace Goodhue Coolidge</a></td>
     <td>office vacant</td>
     </tr>,
     <tr>
     <td><b>1925-1929</b></td>
     <td><a href="057_pra2.html#coolidge">Calvin Coolidge</a></td>
     <td><a href="058_fla1.html#coolidge">Grace Goodhue Coolidge</a></td>
     <td><a href="059_vpa2.html#dawes">Charles G. Dawes</a></td>
     </tr>,
     <tr>
     <td><b>1929-1933</b></td>
     <td><a href="057_pra3.html#hoover">Herbert Hoover</a></td>
     <td><a href="058_fla3.html#hoover">Lou Henry Hoover</a></td>
     <td><a href="059_vpa2.html#curtis">Charles Curtis</a></td>
     </tr>,
     <tr>
     <td><b>1933-1941</b></td>
     <td><a href="057_pra5.html#rooseveltf">Franklin D. Roosevelt</a></td>
     <td><a href="058_fla4.html#rooseveltel">Eleanor Roosevelt</a></td>
     <td><a href="059_vpa2.html#garner">John N. Garner</a></td>
     </tr>,
     <tr>
     <td><b>1941-1945</b></td>
     <td><a href="057_pra5.html#rooseveltf">Franklin D. Roosevelt</a></td>
     <td><a href="058_fla4.html#rooseveltel">Eleanor Roosevelt</a></td>
     <td><a href="059_vpa4.html#wallace">Henry A. Wallace</a></td>
     </tr>,
     <tr>
     <td><b>1945</b></td>
     <td><a href="057_pra5.html#rooseveltf">Franklin D. Roosevelt</a></td>
     <td><a href="058_fla4.html#rooseveltel">Eleanor Roosevelt</a></td>
     <td><a href="059_vpa4.html#truman">Harry S. Truman</a></td>
     </tr>,
     <tr>
     <td><b>1945-1949</b></td>
     <td><a href="057_pra6.html#truman">Harry S. Truman</a></td>
     <td><a href="058_fla4.html#truman">Bess Wallace Truman</a></td>
     <td>office vacant</td>
     </tr>,
     <tr>
     <td><b>1949-1953</b></td>
     <td><a href="057_pra6.html#truman">Harry S. Truman</a></td>
     <td><a href="058_fla4.html#truman">Bess Wallace Truman</a></td>
     <td><a href="059_vpa1.html#barkley">Barkley, Alben W.</a></td>
     </tr>,
     <tr>
     <td><b>1953-1961</b></td>
     <td><a href="057_pra2.html#eisenhower">Dwight D. Eisenhower</a></td>
     <td><a href="058_fla2.html#eisenhower">Mamie Doud Eisenhower</a></td>
     <td><a href="059_vpa3.html#nixon">Richard M. Nixon</a></td>
     </tr>,
     <tr>
     <td><b>1961-1963</b></td>
     <td><a href="057_pra4.html#kennedy">John F. Kennedy</a></td>
     <td><a href="058_fla3.html#kennedy">Jacqueline Kennedy</a></td>
     <td><a href="059_vpa3.html#johnsonl">Lyndon B. Johnson</a></td>
     </tr>,
     <tr>
     <td><b>1963-1965</b></td>
     <td><a href="057_pra4.html#johnsonl">Lyndon B. Johnson</a></td>
     <td><a href="058_fla3.html#johnsonl">Lady Bird Johnson</a></td>
     <td>office vacant</td>
     </tr>,
     <tr>
     <td><b>1965-1969</b></td>
     <td><a href="057_pra4.html#johnsonl">Lyndon B. Johnson</a></td>
     <td><a href="058_fla3.html#johnsonl">Lady Bird Johnson</a></td>
     <td><a href="059_vpa3.html#humphrey">Hubert H. Humphrey</a></td>
     </tr>,
     <tr>
     <td><b>1969-1973</b></td>
     <td><a href="057_pra5.html#nixon">Richard M. Nixon</a></td>
     <td><a href="058_fla3.html#nixon">Pat Nixon</a></td>
     <td><a href="059_vpa1.html#agnew">Spiro T. Agnew</a></td>
     </tr>,
     <tr>
     <td><b>1973-1974</b></td>
     <td><a href="057_pra5.html#nixon">Richard M. Nixon</a></td>
     <td><a href="058_fla3.html#nixon">Pat Nixon</a></td>
     <td><a href="059_vpa2.html#ford">Gerald R. Ford</a></td>
     </tr>,
     <tr>
     <td><b>1974-1977</b></td>
     <td><a href="057_pra2.html#ford">Gerald R. Ford</a></td>
     <td><a href="058_fla2.html#ford">Betty Ford</a></td>
     <td><a href="059_vpa3.html#rockefeller">Nelson Rockefeller</a></td>
     </tr>,
     <tr>
     <td><b>1977-1981</b></td>
     <td><a href="057_pra1.html#carter">Jimmy Carter</a></td>
     <td><a href="058_fla1.html#carter">Rosalynn Carter</a></td>
     <td><a href="059_vpa3.html#mondale">Walter F. Mondale</a></td>
     </tr>,
     <tr>
     <td><b>1981-1989</b></td>
     <td><a href="057_pra5.html#reagan">Ronald Reagan</a></td>
     <td><a href="058_fla4.html#reagan">Nancy Reagan</a></td>
     <td><a href="059_vpa1.html#bush">George Bush</a></td>
     </tr>,
     <tr>
     <td><b>1989-1993</b></td>
     <td><a href="057_pra1.html#bush">George Bush</a></td>
     <td><a href="058_fla1.html#bush">Barbara Bush</a></td>
     <td><a href="059_vpa3.html#quayle">Dan Quayle</a></td>
     </tr>,
     <tr>
     <td><b>1993-2001</b></td>
     <td><a href="057_pra2.html#clinton">Bill Clinton</a></td>
     <td><a href="058_fla1.html#clinton">Hillary Rodham Clinton</a></td>
     <td><a href="059_vpa2.html#gore">Albert Gore</a></td>
     </tr>,
     <tr>
     <td><b>2001-2009</b></td>
     <td><a href="057_pra1.html#bushgw">George W. Bush</a></td>
     <td><a href="058_fla1.html#bushl">Laura Bush</a></td>
     <td><a href="../info/gwbushinfo.html">Richard Cheney</a></td>
     </tr>,
     <tr>
     <td><b>2009-2017</b></td>
     <td><a href="057_pra5.html#obama">Barack Obama</a></td>
     <td><a href="058_fla3.html#obama">Michelle Obama</a></td>
     <td><a href="059_vpa1.html#biden">Joseph R. Biden</a></td>
     </tr>,
     <tr>
     <td><b>2017-2021</b></td>
     <td><a href="057_pra6.html#trump">Donald J. Trump</a></td>
     <td><a href="058_fla4.html#trump">Melania Trump</a></td>
     <td><a href="059_vpa3.html#pence">Mike Pence</a></td>
     </tr>,
     <tr>
     <td><b>2021-</b></td>
     <td><a href="057_pra1.html#biden">Joseph R. Biden</a></td>
     <td><a href="058_fla1.html#biden">Jill Biden</a></td>
     <td><a href="059_vpa2.html#harris">Kamala Harris</a></td>
     </tr>,
     <tr align="center">
     <td><strong>Presidents:</strong> <a href="057_intr.html">Introduction (Rights/Ordering
           Info.)</a> | <a href="057_pra1.html">Adams
             - Cleveland</a> | <a href="057_pra2.html">Clinton - Harding</a> <br/>
     <a href="057_pra3.html">Harrison
             - Jefferson</a> | <a href="057_pra4.html">Johnson - McKinley</a> | <a href="057_pra5.html">Monroe
               - Roosevelt</a> | <a href="057_pra6.html">Taft - Trump</a> | <a href="057_pra7.html">Tyler
                 - Wilson</a><br/>
     <a href="057_pral.html">List of names, Alphabetically</a> | <a href="057_chron.html">List
             of names, Chronologically</a></td>
     </tr>,
     <tr align="center">
     <td><strong>First Ladies</strong>: <a href="058_intr.html">Introduction
           (Rights/Ordering Info.)</a> | <a href="058_fla1.html">Adams
             - Coolidge</a> | <a href="058_fla2.html">Eisenhower - Hoover<br/>
     </a><a href="058_fla3.html">Jackson
                 - Pierce</a> | <a href="058_fla3.html"></a> <a href="058_fla4.html">Polk - Wilson</a> | <a href="058_flal.html">List
                   of names, Alphabetically</a></td>
     </tr>,
     <tr align="center">
     <td> <strong>Vice Presidents:</strong> <a href="059_vp_intr.html">Introduction (Rights/Ordering Info.)</a> | <a href="059_vpa1.html">Adams - Coolidge</a> | <a href="059_vpa2.html">Curtis - Hobart</a> <br/>
     <a href="059_vpa3.html">Humphrey - Rockefeller</a> | <a href="059_vpa4.html">Roosevelt - Wilson</a><br/>
     <a href="059_vp_alpha.html">List of names, Alphabetically</a> | <a href="057_chron.html">List of names, Chronologically</a></td>
     </tr>,
     <tr valign="top">
     <td><a href="#top"><img align="left" alt="Top of Page" border="0" height="22" src="../images/up-button.gif" width="22"/></a> <a href="#top">Top
                   of Page</a> </td>
     </tr>,
     <tr>
     <td bgcolor="#663366"><img alt="" height="1" src="../images/spacer-dkpurple.gif" width="310"/></td>
     <td bgcolor="#663366"><img alt="" height="1" src="../images/spacer-dkpurple.gif" width="430"/></td>
     </tr>,
     <tr bgcolor="#EEEEEE">
     <td bgcolor="#DDDDDD">   <a href="//www.loc.gov/rr/print/">Home</a> &gt;&gt; <!-- InstanceBeginEditable name="bottombreadcrumb" -->
     <a href="listguid.html">Image Lists</a> &gt;&gt; <a href="057_intr.html">Presidents</a><!-- InstanceEndEditable --></td>
     <td align="right" bgcolor="#DDDDDD">
     <!-- InstanceBeginEditable name="bottomsearchbox" -->
     <form action="http://search.loc.gov:8765/query.html" method="GET" name="seek" style="margin-bottom:0;">
     <table bgcolor="#DDDDDD" border="0" cellpadding="4" cellspacing="0">
     <tr>
     <td align="right" height="32"><label for="find2">Find</label></td>
     <td><input name="col" type="hidden" value="loc"/>
     <input id="find2" maxlength="255" name="qt" size="15" style="font-family: monospace; font-size: 12px" tabindex="1" type="text" value=""/>
     </td>
     <td><label for="in2">in</label></td>
     <td><span class="drop-box">
     <select id="in2" name="qp" size="1" tabindex="2">
     <option selected="" value="url:/rr/print/list/">Image Lists</option>
     <option value="url:/rr/print/">Prints and Photographs Pages</option>
     <option value="url:/rr/ url:/cfbook/ url:/poetry/ url:/folklife/ url:/loc/kluge/">Researchers
                     Web Pages</option>
     <option value="">All Library of Congress Pages</option>
     </select>
     </span></td>
     <td align="left"><input align="top" alt="go" class="submit" name="submit" src="../images/go-button.gif" tabindex="3" type="image"/>
     </td>
     </tr>
     </table>
     </form>
     <!-- InstanceEndEditable --></td>
     </tr>,
     <tr>
     <td align="right" height="32"><label for="find2">Find</label></td>
     <td><input name="col" type="hidden" value="loc"/>
     <input id="find2" maxlength="255" name="qt" size="15" style="font-family: monospace; font-size: 12px" tabindex="1" type="text" value=""/>
     </td>
     <td><label for="in2">in</label></td>
     <td><span class="drop-box">
     <select id="in2" name="qp" size="1" tabindex="2">
     <option selected="" value="url:/rr/print/list/">Image Lists</option>
     <option value="url:/rr/print/">Prints and Photographs Pages</option>
     <option value="url:/rr/ url:/cfbook/ url:/poetry/ url:/folklife/ url:/loc/kluge/">Researchers
                     Web Pages</option>
     <option value="">All Library of Congress Pages</option>
     </select>
     </span></td>
     <td align="left"><input align="top" alt="go" class="submit" name="submit" src="../images/go-button.gif" tabindex="3" type="image"/>
     </td>
     </tr>,
     <tr>
     <td colspan="2"><table border="0" cellpadding="0" cellspacing="0" width="760">
     <tr>
     <td bgcolor="#663366" height="40" width="37%">  <a class="white" href="//www.loc.gov/">The
               Library of Congress</a> <span class="white-text">&gt;&gt;</span> <a class="white" href="//www.loc.gov/rr/">Researchers</a><br/>
     <span class="white-text"> 
                 <!-- #BeginDate format:Am1 -->December 21, 2020<!-- #EndDate -->
     </span></td>
     <td align="center" bgcolor="#663366" width="38%"><a class="white" href="//www.loc.gov/homepage/legal.html">Legal</a> <span class="white-text">|</span> <a class="white" href="//www.loc.gov/global/disclaim.html">External Link Disclaimer</a><br/>
     <br/></td>
     <td align="right" bgcolor="#663366" height="40" width="25%"><a class="white" href="//www.loc.gov/rr/askalib/ask-print.html">Contact
               Us: </a> <br/>
     <a class="white" href="//www.loc.gov/rr/askalib/ask-print.html">Ask
                 a Librarian</a>  </td>
     </tr>
     </table></td>
     </tr>,
     <tr>
     <td bgcolor="#663366" height="40" width="37%">  <a class="white" href="//www.loc.gov/">The
               Library of Congress</a> <span class="white-text">&gt;&gt;</span> <a class="white" href="//www.loc.gov/rr/">Researchers</a><br/>
     <span class="white-text"> 
                 <!-- #BeginDate format:Am1 -->December 21, 2020<!-- #EndDate -->
     </span></td>
     <td align="center" bgcolor="#663366" width="38%"><a class="white" href="//www.loc.gov/homepage/legal.html">Legal</a> <span class="white-text">|</span> <a class="white" href="//www.loc.gov/global/disclaim.html">External Link Disclaimer</a><br/>
     <br/></td>
     <td align="right" bgcolor="#663366" height="40" width="25%"><a class="white" href="//www.loc.gov/rr/askalib/ask-print.html">Contact
               Us: </a> <br/>
     <a class="white" href="//www.loc.gov/rr/askalib/ask-print.html">Ask
                 a Librarian</a>  </td>
     </tr>]



## Get the column labels

The first row is the column header row as can be seen by running the following code:




    <tr valign="top">
    <td bgcolor="#663366" colspan="2" height="25"><a href="#content" name="top"><img alt="Skip Navigation Links" border="0" height="1" src="../images/spacer-dkpurple.gif" width="1"/></a>  <a class="white" href="//www.loc.gov/">The
            Library of Congress</a> <span class="white-text">&gt;&gt;</span> <a class="white" href="//www.loc.gov/rr/">Researchers</a></td>
    </tr>








    []



## Parse Rows

&#9989; **<font color=red>DO THIS:</font>** The next step is to loop though the remaining rows and save the data as a list of lists

## Convert list of list to Pandas Dataframe

Assuming the above works, we can convert the list of lists and labels to a Pandas Dataframe


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-18-2eb2887b5baf> in <module>
          2 
          3 # Create the pandas DataFrame
    ----> 4 df = pd.DataFrame(data, columns=labels)
    

    NameError: name 'data' is not defined


----

<a name="DynamicWebsites"></a>

# 4. Dynamic Website example

The two above examples were fairly simple. However, sometimes websites get a lot more complex.  This is especially true when the website includes "client side" code.  This code (typically javascript) runs on the web browser in your local computer and not the web server.  It makes the problem difficult because to pull the data out you often need to either figure out what the code is doing and mimic it in your python program or "render" the program using a javascript client and then figure out the output.  


Fortunatly there are tools that can help.  Have your team do a google search and see if you can find some python tools specifically designed to help render dynamic websites.  See if you can download/install and test the code.



---

<a name="Wrapup"></a>


# 5. Wrap-up Discussion

Written by Dr. Dirk Colbry, Michigan State University
<a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/">Creative Commons Attribution-NonCommercial 4.0 International License</a>.

----
