---
title: "NATO Code Translator"
description: "Make you sound smarter cos you are not"
draft: false
image : "images/our-projects/pid002/banner.png"
bg_image: "images/our-projects/pid002/banner.png"
category: []
information:
  - label : "Name"
    info : "NATO Code Translator"
  - label : "Event"
    info : "NA"
  - label : "Event Name"
    info : "NA"
  - label : "Event Detail"
    info : "NA"
  - label : "Team Members"
    info : "Conan"
  - label : "Devpost"
    info : "NA"
  - label : "GitHub"
    info : "NA"
  - label : "Survey Link"
    info : "NA"
---

## Name
### NATO Code Translator

---

## Our Mission
Make you sound smarter cos you are not

---

## App

Put Your Text Here:

<textarea id="input" name="message" class="form-control" rows="4" placeholder="Type text here..." required></textarea>
<br>

Output:
<div class="output" id="output"></div>
<br>
<button class="btn btn-default" onclick="copyText()">Copy</button>

</div>

<script>

const nato = {
A:"Alpha", B:"Bravo", C:"Charlie", D:"Delta", E:"Echo",
F:"Foxtrot", G:"Golf", H:"Hotel", I:"India", J:"Juliett",
K:"Kilo", L:"Lima", M:"Mike", N:"November", O:"Oscar",
P:"Papa", Q:"Quebec", R:"Romeo", S:"Sierra", T:"Tango",
U:"Uniform", V:"Victor", W:"Whiskey", X:"X-ray",
Y:"Yankee", Z:"Zulu"
};

const reverseMap = Object.fromEntries(
Object.entries(nato).map(([k,v])=>[v.toLowerCase(),k])
);

const input = document.getElementById("input");
const output = document.getElementById("output");

input.addEventListener("input", translate);

function translate(){

let text=input.value.toUpperCase();
let words=[];

for(let char of text){

if(nato[char]){
words.push(nato[char]);
}

if(char===" "){
words.push("/");
}

}

output.innerText=words.join(" ");
}

function copyText(){

navigator.clipboard.writeText(output.innerText);

alert("Copied to clipboard");

}

</script>

</body>
</html>



