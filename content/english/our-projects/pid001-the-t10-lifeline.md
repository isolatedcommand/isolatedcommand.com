---
title: "T10 Lifeline"
description: "FIGHTING BRAINROT, ONE MIND AT A TIME"
draft: false
image : "images/our-projects/pid001/banner.png"
bg_image: "images/our-projects/pid001/banner.png"
category: []
information:
  - label : "Name"
    info : "T10 Lifeline"
  - label : "Event"
    info : "Hackathon"
  - label : "Event Name"
    info : "Hack & Roll 2026"
  - label : "Event Detail"
    info : "<a href=https://hacknroll.nushackers.org>Click Here</a>"
  - label : "Team Members"
    info : "Everyone in IC"
  - label : "Devpost"
    info : "<a href=https://devpost.com/software/t10-lifeline>Click Here</a>"
  - label : "GitHub"
    info : "<a href=#>Click Here</a>"
  - label : "Survey Link"
    info : "<a href=#survey>Click Here</a>"
---


## Survey

<iframe width="1000px" height="1000px" src="https://forms.office.com/Pages/ResponsePage.aspx?id=mG4Uve_emker4a2bTgtn_Pfsds4_DThHnKHLlPpKhtxUNE0zTzZHV0hMMjZEQlcxVFdVQUpXQlE0QyQlQCN0PWcu&embed=true" frameborder="0" marginwidth="0" marginheight="0" style="border: none; max-width:100%; max-height:100vh" allowfullscreen webkitallowfullscreen mozallowfullscreen msallowfullscreen> </iframe>

---

## Name
### T10 Lifeline  

---

## Our Mission
### Fighting Brainrot, One Mind at a Time

---

## Target Audience

Mainly youths born in the 2010s (≤16 y/o) who constantly does random scrolling on popular social media platforms (e.g TikTok, Instagram Reels, Youtube Shorts). These group of youths scrolls at an average of 3-5 hours per day. 

## Our app feature

Using AI Chat to fight brainrot.

## What we have identified?
Digital “brainrot” - endless scrolling, low-quality content, and mental overload — is increasingly affecting attention, motivation, and mental clarity. 

Many people want to escape the cycle, but don’t know where to start. Existing tools either overwhelm users or feel too clinical.  

We wanted to create a simple, fun, accessible solution that helps people reset their minds without shame or pressure.

---

## Our Goal

To help people reduce digital brainrot and build healthier thinking habits using a friendly, lightweight web app that blends clarity, accountability, and humour.

## Inspiration
We were inspired by how common the term “brainrot” has become — especially among students and young people who struggle with doomscrolling and focus. We wanted to build something that speaks their language while actually helping them reset and regain clarity.

## App

<div style="max-width:520px;border:1px solid #ddd;border-radius:12px;padding:12px">
  <div id="msgs" style="height:320px;overflow:auto;white-space:pre-wrap"></div>
  <a
  href="https://chatgpt.com/g/g-696c49ebc85881919c6c6e727f690c10-t10-lifeline-app"
  target="_blank"
  rel="noopener noreferrer"
  style="display:inline-block;padding:12px 18px;border-radius:10px;border:1px solid #ddd;text-decoration:none;"
>
  Open T10 Lifeline App
</a>
  <form id="f" style="display:flex;gap:8px;margin-top:10px">
    <input id="t" placeholder="Type here…" style="flex:1;padding:10px;border-radius:10px;border:1px solid #ddd" />
    <button style="padding:10px 14px;border-radius:10px;border:1px solid #ddd">Send</button>
  </form>
</div>

<script>
  const msgs = document.getElementById('msgs');
  const f = document.getElementById('f');
  const t = document.getElementById('t');

  function add(role, text){
    msgs.textContent += `\n${role.toUpperCase()}: ${text}\n`;
    msgs.scrollTop = msgs.scrollHeight;
  }

  f.addEventListener('submit', async (e) => {
    e.preventDefault();
    const text = t.value.trim();
    if (!text) return;
    t.value = '';
    add('user', text);

    const r = await fetch('/api/t10', {
      method: 'POST',
      headers: {'Content-Type':'application/json'},
      body: JSON.stringify({ message: text })
    });

    const data = await r.json();
    add('assistant', data.reply || '(no reply)');
  });
</script>




