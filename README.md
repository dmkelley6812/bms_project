This is part 1 of a Razor MX350 Battery/BMS/Motor Controller build. 

<h1>
  Design Considerations
</h1>
<ul>
  <li><h3>Desired Specs:</h3></li>
  <ul>
    <li><b>System Voltage:</b> 36V</li>
    <li><b>Motor Power:</b> 1000W</li>
    <li><b>Max Current (30% margin):</b> 36A</li>
    <li><b>Desired Run Time at 50% power:</b> 1 hour</li>
    <li><b>Pack size needed to achieve desired run time:</b> .5kWh/13.8Ah</li>
  </ul>
  <li><h3>Component Selection</h3></li>
    <ul>
      <li><b>18650 Cell:</b> EVE 33V 18650 3200mAh 10A Battery</li>
      <li><b>Cell Configuration:</b> 10S5P (36V nominal, 3.2AH*5= 16Ah Capacity)</li>
      <li><b>Protection/Balancing IC:</b> ????</li>
    </ul>
</ul>


<h1>Project Goal</h1>
The goal of this project is to build (from scratch) a Li-Ion battery back, custom BMS, and a PWM motor controller to install in a Razor MX350 dirtbike. 



<h1>Pack Design</h1>
I've chosen a 10S5P 18650 architecture for this build for the following reasons:
<ul>
  <li>10S configuration yields a nominal 36V which is common in Razor dirtbike mods and has a wide range of available DC motors in the 36V 1000W range.</li>
  <li>The 5P configuration was chosen based on the assumption that the bike will, on average, be ridden at 50% of available power. This would result in an average of 500W consumption. 1hr run-time would result in requiring a .5kWh/13.8Ah pack size</li>
  <li>I expect to acquire 3200mAh cells, though I may have to settle for lower capacity cells depending on pricing and availability when ordering. 13.8Ah pack/ 3.2Ah per cell = 4.31 Cells in parallel./li>
</ul>


<h1>BMS Design</h1>
I've gone back and forth over which tech to use in the BMS. I think I've settled on using standalone ICs to handle cell protection, monitoring, and balancing, rather than incorporating an MCU. Given the lower voltage/capacity of this project, I think an MCU would be overkill. I have plans to potentially do another build in the future using a 72V architecture with a 3000 motor. In that build, I will likely upgrade to an MCU to handle the monitoring and reporting of voltages, balancing status, etc. to an external LCD monitor. 

<h3>Component selection</h3>
<ul>
  <li><b>Cell monitoring, Protection, and Balancing:</b> BQ77915 3-Series to 5-Series Stackable Ultra-Low Power Primary Protector with
Autonomous Cell Balancing and HIBERNATE Mode</li>
  <ul>  
    <li>This single IC provides standalone Voltage, Current, and Temperature protections. It also provides 50mA of internal cell balancing current and also supports external FETs for higher balancing current</li>
    <li>Given that this single IC handles essentially all major functions, I don't think I'll do anything additional on this build. The goal is just simple pack protections and balancing. </li>
    <li>I will likely develop the PCB with two of the BQ77915s to support my 10S configuration, and will also incorporate external FETs to support greater than 50mv balancing current.</li>
  </ul>
  
</ul>










