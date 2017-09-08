+++
title = "Remote guru"
lastmod = "2017-08-26"
date = "2017-08-26"
image ="img/ChibiStephContact.svg"
[elements]
  footer = true
  contact = true



[style]
  center = false
+++



Are you or your staff learning data science on the job and need someone to answer architectural or technical questions? Do you need someone you can bounce ideas off and can tell you what's worked in the past in similar projects? 

We can help by being your remote guru! You can email us or hop on a call with us. Get a lead data scientist for your organisation without having to go through the hiring process.

{{<btn href="//itsalocke.com/#contact" msg="Get in touch">}}


## Decide your requirements

### How much access should we have to your systems?

+ **None** If you only need general advice or want to just show via screenshare then we don't need to do any setup
+ **Exports** If you want to be able to send us data and we need to spend some time agreeing how the data will be handled
+ **Remote access** If you want us to be able to login to your systems to be able to do stuff then we need to work with you to get and test that access

<style> 
.slider {
  -webkit-appearance: none;
  width: 100%;
  height: 15px;
  border-radius: 5px;
  background: #d3d3d3;
  outline: none;
  opacity: 0.7;
  -webkit-transition: .2s;
  transition: opacity .2s;
}
.slider::-webkit-slider-thumb {
  -webkit-appearance: none;
  appearance: none;
  width: 25px;
  height: 25px;
  border-radius: 50%;
  background: #2165B6;
  cursor: pointer;
}
</style>
<div id="slidecontainer">
  <input type="range" min="1" max="3" value="1" class="slider" id="setup">
  <p>Selected: <span id="setupcost"></span></p>
</div>

### How often will you need us?
+ **Just the once** For something that comes up out of the blue
+ **Occasionally** For just one or two things a month
+ **Often** For things that come up weekly - maybe a small team who knows their stuff or one person who needs support
+ **A lot** For on-tap support for a team learning their craft

<div id="slidecontainer">
  <input type="range" min="1" max="4" value="2" class="slider" id="engagement">
  <p>Selected: <span id="engagementcost"></span></p>
</div>

### What timezones do you need us to work on?
We like our beauty sleep! When do you need us to be available?

- **UK hours** 9am - 7pm GMT
- **Other hours** Need us during full US hours for instance?

<div id="slidecontainer">
  <input type="range" min="1" max="2" value="1" class="slider" id="tz" onChange="updatePrice()">
  <p>Selected: <span id="tzmult"></span></p>
</div>

### What turnaround time do you need? 
+ **It can wait!** Schedule calls or get email support within four business days
+ **Need it soon** Schedule calls or get email support within two business days
+ **Need it now** Schedule calls or get email support within a business day

<div id="slidecontainer">
  <input type="range" min="1" max="3" value="1" class="slider" id="sla" onChange="updatePrice()">
  <p>Value: <span id="slaval"></span></p>
</div>

## Quote
Based on your requirements, here's what having us available <span id="monthlyhours"></span> hours a month to be your remote guru would cost:

- One-off setup costs will be £<span id="setupcosts"></span>
- Monthly costs will be £<span id="monthlycosts"></span>
- Get extra time if needed at £<span id="monthlyextra"></span> per extra hour

{{<btn href="//itsalocke.com/#contact" msg="Get in touch">}}

## How prices are calculated
Here's a break down of how prices are calculated.

### Setup costs
Depending on how much access you need us to have, we'll need to spend some time doing initial setup work with you. 

| Level         | Cost |
|---------------|-----:|
| No access     | £0   |
| Exports       | £250 |
| Remote access | £500 |

### Usage
Here are base monthly prices.

| Level           | Hours included |   Cost | Extra hours |
|-----------------|---------------:|-------:|------------:|
| Just the once   |              0 |     £0 |        £250 |
| Occasional use  |              2 |   £400 |        £200 |
| Often           |              5 |   £875 |        £175 |
| A lot           |             10 | £1,500 |        £150 |

### Core hours
Being available outside of UK working hours plays havoc on the social life. As a result, we charge a bit more if you want us to be available  late at night or very early.

| Timezons      | Multiplier |
|--------------|-------:|
| UK hours is fine  |   1.0x |
| Other hours |   1.4x |

### Urgency
We're a jetsetting bunch with clients all over the place so flexibility is great for us. The sooner you need us, the less flexible we can be overall so there's a premium associated with how quickly you need us to turnaround answers or jump on calls with you.

| Urgency      | Multiplier  |
|--------------|-------:|
| It can wait  |   1.0x |
| Need it soon |   1.2x |
| Need it now  |   1.4x |


## Get started
If you want to to kick off a discussion about getting us to be your remote guru, use our form.

{{<btn href="//itsalocke.com/#contact" msg="Get in touch">}}

<script>
//Ref data
var setupopts = [
  "No access",
  "Exports",
  "Remote access"
];
var setupcosts = [0, 250, 500];

var engagementopts = [
  "Just the once",
  "Occassionally",
  "Often",
  "A lot"
];
var engagementcosts = [0, 400, 875, 1500];
var engagementhours = [0, 2, 5, 10];
var engagementhourly = [250, 200, 175, 150];

var tzopts = [
  "UK hours",
  "Other hours"
];
var tzscale = [1, 1.4];

var slaopts = [
  "It can wait!",
  "Need it soon",
  "Need it now"
];
var slaval = [1, 1.2, 1.4];

// Sliders
var setup = document.getElementById("setup");
var engagement = document.getElementById("engagement");
var tz = document.getElementById("tz");
var sla = document.getElementById("sla");

// Labels
var setupoutput = document.getElementById("setupcost");
var engagementoutput = document.getElementById("engagementcost");
var tzoutput = document.getElementById("tzmult");
var slaoutput = document.getElementById("slaval");

// Calculated variables
var setupout = document.getElementById("setupcosts");
var monthout = document.getElementById("monthlycosts");
var hourout = document.getElementById("monthlyhours");
var hourcosts = document.getElementById("monthlyextra");

// Defaults
setupoutput.innerHTML = setupopts[0];
engagementoutput.innerHTML = engagementopts[1];
tzoutput.innerHTML = tzopts[0];
slaoutput.innerHTML = slaopts[0];
setupout.innerHTML = setupcosts[0];
monthout.innerHTML = engagementcosts[1];
hourout.innerHTML = engagementhours[1];
hourcosts.innerHTML = engagementhourly[1];

// Calculation
function updatePrice(tz, sla, eng) {
  var scale = tzscale[tz.value - 1] * slaval[sla.value - 1];
  var engpos = eng.value - 1;
  monthout.innerHTML = Math.round(scale * engagementcosts[engpos]).toLocaleString();
  hourout.innerHTML = engagementhours[engpos];
  hourcosts.innerHTML = Math.round(scale * engagementhourly[engpos]);
};

// Updating sliders
setup.oninput = function() {
  setupoutput.innerHTML = setupopts[this.value - 1];
  setupout.innerHTML = setupcosts[this.value - 1];
};

engagement.oninput = function() {
  engagementoutput.innerHTML = engagementopts[this.value - 1];
  updatePrice(tz, sla, this);
};

tz.oninput = function() {
  tzoutput.innerHTML = tzopts[this.value - 1];
  updatePrice(this, sla, engagement);
};

sla.oninput = function() {
  slaoutput.innerHTML = slaopts[this.value - 1];
  updatePrice(tz, this, engagement);
};

</script>