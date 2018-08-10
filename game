var lexicon;
var points = 0;
var nextWord;
var start;
var yesButton;
var noButton;

function setup() {
	createCanvas(windowWidth, windowHeight);
	background(255);
	lexicon = new RiLexicon();
	textFont("Times New Roman");
	textSize(72);
	textAlign(CENTER);
	fill(0);
 	textSize(30);
	start = createButton("Click to start");
 	start.position(width/2-100, height/2);
	start.mousePressed(mainGame);
}

class Word {
	constructor(){
		this.xpos = width/2;
		this.ypos = height/3;
		this.word = lexicon.randomWord();
		this.choice = Math.round(Math.random()); //0 or 1
		
	}
	
	display(){ //new randomization, when next game
		
		textSize(100);
		text(this.word, this.xpos, this.ypos);
		textSize(30);
		var wordSpeech = new p5.Speech();
		var tempArr = lexicon.similarBySound(this.word);
		var similarWord = tempArr[Math.floor(Math.random() * tempArr.length)];
		var randomWord = [this.word, similarWord]; //original vs similar
		wordSpeech.speak(randomWord[this.choice]);
	}
}

function mainGame() {
	start.remove();
	yesButton = createButton("Yes");
	noButton = createButton("No");
	background(random(200,255),random(200,255),random(200,255));
	textSize(30);
	text("Points: " + points,100,100);
	
	nextWord = new Word;
	nextWord.display();
	
	yesButton.position(width/2-100, height/2);
	noButton.position(width/2+100, height/2);
	if (nextWord.choice === 0) { //if text and sound matches
		yesButton.mousePressed(adder);
		noButton.mousePressed(restart);
	} else if (nextWord.choice === 1) { //if text not the same as sound
		noButton.mousePressed(adder);
		yesButton.mousePressed(restart);
	}
	
}
function adder(){
	points++;
	mainGame();
}

function restart(){
	points = 0;
	yesButton.remove();
	noButton.remove();
	background(255,255,255);
	start = createButton("You lost. It's okay. Click here to try again.");
	start.position(width/2-100, height/2);
	start.mousePressed(mainGame);
}
