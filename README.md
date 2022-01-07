# The maple cheatsheat

## About the project

It all started when i needed to combine two plots, quite simple i thought, just a pointplot and a graph. But then! I saw the maple wiki and i started crying (i didnt) Then i told myself i would proper write some easy to navigate open source documentation that is avaliable to everyone :ooo

This also means it's completely a community driven project, any help in catching errors, explaing on already knowen knolage and comming up with new stuff is always great. You can simply create a Pull Request and i will review it 😄

<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#installation">Installation Guide</a></li>
    <li><a href="#plots">Plots</a></li>
      Axis ranges - Lables - Gridlines - Axis arrows  
    <li><a href="#Units">Units in maple</a></li>
    <li><a href="#Tables">Tables</a></li>
    <li><a href="#page-setup-in-maple">Page setup (headers and footers)</a></li>
  </ol>
</details>

## Installation

Maple is avaliable for **linux**, **windows** and **mac**

<details closed="closed">
  <summary><b>Installing on linux</b></summary>
  Head over to <a href=https://www.maplesoft.com/download/>this link</a> and download the installation files for linux (you need a product key)
  
  After this step we need to make the file executable using the `chmod` command in your terminal
  ```
  chmod +x <path to file>
  ```
  And now simply run the file, you can use a graphical file manager to run it or use `./` in the command line
  
  <b>If you get a Missing host ID for license server error</b> it may be because you are missing one of the `lsb` packages
  
  Install one of the following packages using your systems package manager
  <ul>
    <li>glibc.i686</li>
    <li>ia32-libs</li>
    <li>ld-lsb</li>
    <li>libc6-i386</li>
    <li>libc6:i386</li>
    <li>libstdc++6:i386</li>
    <li>lsb</li>
    <li>lsb-base</li>
    <li>lsb-core</li>
  </ul>
  
  At last you should also install the gym package
  Install it from [this link](https://www.maplesoft.com/dk/MapleGym/index.aspx) you should follow the same steps from above, making it executable using chmod and running the setup file
  
</details>
<details closed="closed">
  <summary><b>Installing on Windows</b></summary>
  Head over to <a href=https://www.maplesoft.com/download/>The maple download page</a> and download the installation files for windows (you need a product key)

  Now we want to run the file we just downloaded, you most likely dont want to use a proxy server

  Once done we want to install the Gym package
  Get it [here](https://www.maplesoft.com/dk/MapleGym/index.aspx) and run that file as well, it will get some nice features we will be covering soon
</details>
  

## Plots

In maple the plot function takes well, a function and some settings arguments
```
f(x) := 3x+4
plot(f(x))
```
<details closed="closed">
  <summary><b>Show result</b></summary>
  <p align="center"><img src='https://user-images.githubusercontent.com/56993729/148114180-3972c80e-1fbe-4a05-8302-f9bedf3cbb3c.png'></p>
</details>  

This is the most basic graph you can plot in maple  
Now we can also include some arguments, here is a small list

1. **Setting lables**  
   Here we use the labels and labeldirections to set lables, label directions tell you want direction each lable should go in, in order. 
   ```
   plot(f(x), labels = ["Årstal", "Antal personer"], labeldirections = [horizontal, vertical])
   ```  
   <details closed="closed">
     <summary><b>Show result</b></summary>
     <p align="center"><img src='https://user-images.githubusercontent.com/56993729/148114326-c58c069b-ebb7-45f3-938e-4cc9f4149b66.png'></p>
   </details>  
  
2. **Setting axis rages**  
   In maple we can also specify the range of each axis, we do this using the following
   ```
   plot(f(x), x=3.. 6)
   ```  
   <details closed="closed">
     <summary><b>Show result</b></summary>
     <p align="center"><img src='https://user-images.githubusercontent.com/56993729/148114702-0611a4ef-0f5d-47a5-a80d-b8f330a4a238.png'></p>
   </details>  
   This will make the x axis go from 3 to 6, you can do the same with the y axis, even at the same time
   
3. **Gridlines**  
    Maple does infact support gridlines, we want to click the plot we want to interact with then on the top there is a button to enable grid lines
    
    <p align="center"><img src='https://user-images.githubusercontent.com/56993729/148176392-c4cea77f-fcd0-4d40-9236-f6e9dd29a9a0.png'></p>

    <details closed="closed">
     <summary><b>Show result</b></summary>

     <p align="center"><img src='https://user-images.githubusercontent.com/56993729/148176570-cad093f9-bf89-4835-acb2-bdd73532cc0b.png'></p>
   </details>  

4. **Axis arrows**  
   Maple on its own does not have support for automatic axis arrows, this means that we have to construct them ourselves, i made a small example / script below and will describe it in more detail whats going on.
   
   ```
   x__min := -10: x__max := 20: y__min := -40: y__max := 40:
   graph := plot(f(x), x = x__min .. x__max, y = y__min .. x__max):
   arrow__1 := plots:-arrow([0, y__max], [0, 0.01], shape = arrow, head_width = 25/y__max, head_length = 20/x__max):
   arrow__2 := plots:-arrow([x__max, 0], [0.01, 0], shape = arrow, head_width = 25/x__max, head_length = 20/y__max):
   plots:-display(graph, arrow__1, arrow__2)
   ```
    <details closed="closed">
     <summary><b>Show result</b></summary>

     <p align="center"><img src='https://user-images.githubusercontent.com/56993729/148609184-227df5e6-0428-47f9-893a-4996cc66cf9b.png'></p>
   </details>  

   Now this geneus code will create two arrows at the end of each of the axis (see the example by clicking expand)
   
   The first line you can edit the range variables to see the exact area you want to view, the arrows get calculated from those values  
   Second line is the graph itself, you can change the `f(x)` part to what ever graph you want to display  
   Line 3 and 4 is displaying the arrows, towards the end we have some divisions, you can change those to change the look feel and size of the arrows  
   And lastly we just display the plot

All of these tricks and even be combined to one great plot

## Units

Maple is able to work with units and with the conversion to SI, this is extremely helpfull to prevent human errors in conversions.

Maple has as deafult limited knowlage of units (sometimes has a hard time converting) You want to use the units librarry, `with(Units):` *where the colon mutes the output*  

An output without importing units will make it look something like this  
<p align="center"><img src='https://user-images.githubusercontent.com/56993729/147928159-c64a4829-4928-4a2a-8647-d078148858e2.png'></p>

When defining a unit we use the `Unit('kg')` function or from the clickable math window called units  
<p align="center"><img src='https://user-images.githubusercontent.com/56993729/148029554-a447dabb-dbb3-4600-8f23-33564f57ac6c.png'></p>

If after you have been using some units still get the isse we discribed before you need to selecet SI from the right pane to make it convert the units

## Tables

In maple, when we need to display a lot of data we can use a table  
<p align="center"><img src='https://user-images.githubusercontent.com/56993729/148063647-c1b061b3-a94f-4894-af3c-f0cd30142ec0.png'></p>

Go to `insert` » `Table` at the top bar and you can choose the size of set table

To expand the table after the creation of it right click the edges of it and you can insert new rows / colums

## Page setup in maple

Page setup in maple is quite a nice thing, when we need to deliver an essay it is very eazy to simply press "export as pdf", this will mean that we are missing a few cursial components such as **headers** and **footers**

To setup a header or a footer go to `insert` » `header footer` and you can set them up as you wish. I recommend using a footer such as `Page &[Page] of &[Pages]`
