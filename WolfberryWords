// WolfberryWords - Word of the Day Widget
// by @WolfberryWords
// Install via Scriptable (free on App Store)
//
// HOW TO INSTALL:
// 1. Download Scriptable from the App Store (free)
// 2. Open Scriptable, tap + and paste this entire script
// 3. Name it WolfberryWords
// 4. Long-press your home screen, tap Edit, tap Add Widget
// 5. Search Scriptable, choose Medium size, select WolfberryWords

// YOUR SERVER URL - update this after Netlify deployment
const API_URL = "https://cheerful-hummingbird-cb5c1a.netlify.app/.netlify/functions/word";

// THEME - change to: original, forest, blood, charcoal, evergreen, black, ivory
const THEME = "original";

const THEMES = {
  original:  { bg: "#1a1410", border: "#c9a84c", word: "#f2ead8", phonetic: "#e2c97e", pos: "#c9a84c", def: "#e8dcc8", account: "#c9a84c" },
  forest:    { bg: "#1a2b1e", border: "#c9a84c", word: "#f2ead8", phonetic: "#e2c97e", pos: "#c9a84c", def: "#e8dcc8", account: "#c9a84c" },
  blood:     { bg: "#2a0a0a", border: "#c9a84c", word: "#f2ead8", phonetic: "#e2c97e", pos: "#c9a84c", def: "#e8dcc8", account: "#c9a84c" },
  charcoal:  { bg: "#1e1e1e", border: "#c9a84c", word: "#f2ead8", phonetic: "#e2c97e", pos: "#c9a84c", def: "#e8dcc8", account: "#c9a84c" },
  evergreen: { bg: "#0d352a", border: "#c9a84c", word: "#f2ead8", phonetic: "#e2c97e", pos: "#c9a84c", def: "#e8dcc8", account: "#c9a84c" },
  black:     { bg: "#000000", border: "#c9a84c", word: "#f2ead8", phonetic: "#e2c97e", pos: "#c9a84c", def: "#e8dcc8", account: "#c9a84c" },
  ivory:     { bg: "#f5f0e8", border: "#7a4f20", word: "#1e140a", phonetic: "#5c3d18", pos: "#7a4f20", def: "#2e200e", account: "#7a4f20" },
};

const C = THEMES[THEME] || THEMES.original;

// Fetch today's word from server
let entry = {
  word: "WolfberryWords",
  phonetic: "/ loading /",
  pos: "noun",
  definition: "A glossary in progress."
};

try {
  const req = new Request(API_URL);
  req.timeoutInterval = 10;
  const data = await req.loadJSON();
  if (data && data.word) entry = data;
} catch(e) {
  // If offline or error, show fallback message
  entry = {
    word: "Offline",
    phonetic: "/ of-LINE /",
    pos: "noun",
    definition: "Connect to the internet to load today's word."
  };
}

// Build widget
const widget = new ListWidget();
widget.backgroundColor = new Color(C.bg);
widget.setPadding(20, 22, 20, 22);
widget.url = "https://www.instagram.com/wolfberrywords/";

// Account name
const accountText = widget.addText("@WolfberryWords");
accountText.font = new Font("Georgia", 11);
accountText.textColor = new Color(C.account, 0.7);
accountText.centerAlignText();

widget.addSpacer(6);

// Top divider
const divStack = widget.addStack();
divStack.layoutHorizontally();
divStack.addSpacer();
const divLine = divStack.addStack();
divLine.size = new Size(160, 1);
divLine.backgroundColor = new Color(C.border, 0.4);
divStack.addSpacer();

widget.addSpacer(8);

// Part of speech
const posText = widget.addText(entry.pos);
posText.font = Font.italicSystemFont(11);
posText.textColor = new Color(C.pos, 0.85);
posText.centerAlignText();

widget.addSpacer(5);

// Word
const wordText = widget.addText(entry.word);
wordText.font = new Font("Georgia", 19);
wordText.textColor = new Color(C.word);
wordText.centerAlignText();

widget.addSpacer(4);

// Phonetic
const phoneticText = widget.addText(entry.phonetic);
phoneticText.font = Font.italicSystemFont(11);
phoneticText.textColor = new Color(C.phonetic, 0.85);
phoneticText.centerAlignText();

widget.addSpacer(10);

// Mid divider
const div2Stack = widget.addStack();
div2Stack.layoutHorizontally();
div2Stack.addSpacer();
const div2Line = div2Stack.addStack();
div2Line.size = new Size(100, 1);
div2Line.backgroundColor = new Color(C.border, 0.35);
div2Stack.addSpacer();

widget.addSpacer(12);

// Definition
const defText = widget.addText(entry.definition);
defText.font = new Font("Georgia", 12);
defText.textColor = new Color(C.def, 0.92);
defText.centerAlignText();
defText.lineLimit = 5;

widget.addSpacer(12);

// Run
if (config.runsInWidget) {
  Script.setWidget(widget);
} else {
  await widget.presentMedium();
}

Script.complete();
