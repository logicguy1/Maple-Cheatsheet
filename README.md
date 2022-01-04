# The maple cheatsheat


<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#installation">Installation Guide</a></li>
    <li><a href="#plots">Plots</a></li>
    <li><a href="#Units">Units in maple</a></li>
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
Now we can also include some arguments, here is a small list

1. **Setting lables**  
   Here we use the labels and labeldirections to set lables, label directions tell you want direction each lable should go in, in order. 
   ```
   plot(f(x), labels = ["Årstal", "Antal personer"], labeldirections = [horizontal, vertical])
   ```
2. **Setting axis rages**  
   In maple we can also specify the range of each axis, we do this using the following
   ```
   plot(f(x), x=3.. 6)
   ```
   This will make the x axis go from 3 to 6, you can do the same with the y axis, even at the same time
   
All of these tricks and even be combined to one great plot

## Units

Maple is able to work with units and with the conversion to SI, this is extremely helpfull to prevent human errors in conversions.

Maple has as deafult limited knowlage of units (sometimes has a hard time converting) You want to use the units librarry, `with(Units):` *where the colon mutes the output*  

An output without importing units will make it look something like this  
![image](https://user-images.githubusercontent.com/56993729/147928159-c64a4829-4928-4a2a-8647-d078148858e2.png)

When defining a unit we use the `Unit('kg')` function or from the clickable math window called units  
![image](https://user-images.githubusercontent.com/56993729/148029554-a447dabb-dbb3-4600-8f23-33564f57ac6c.png)

If after you have been using some units still get the isse we discribed before you need to selecet SI from the right pane to make it convert the units
