-----------------------------------------------------------------------------------------
--
-- main.lua
--
-----------------------------------------------------------------------------------------

local pop = audio.loadSound( "pop.mp3" )
local pop1 = audio.loadSound( "pop1.mp3" )
local pop2 = audio.loadSound( "pop2.mp3" )

highScore = 0
local btnclick1,btnclick2,btnclick3,btnclick4,btnclick5,btnclick6,btnclick7,btnclick8,btnclick9
local pat = {};
local round = 1;
local go
local checker = 0
i = 0;
local light
local pattern = {}
local restartButton;
local deletingbits;
snakebits = {}
local textStart
local patternIndex
gameOver = true
math.randomseed(os.time())

local function reset(event)
 pattern = {}
 round = 1
 checker = 0
 i = 0
 rate = 2
 restartButton:removeSelf();
 gameOver = false;
 timer.performWithDelay(1000,go)

end


local function setup()
-->Adds background image
background = display.newImage("wallpaper.jpg")
background.x = display.contentWidth/1
background.y = display.contentHeight/2
background:scale(.8,.9)


 -->Adds Boxes - row 1
box1 = display.newImage("my_box.png")
box1.x = display.contentWidth/5
box1.y = display.contentWidth/2
box1: scale(.285,.285)
btnclick1 = display.newImage("bluebox.png")
btnclick1: scale(.85,.85)
btnclick1.x = display.contentWidth/5
btnclick1.y = display.contentHeight/3
btnclick1.id = 1



box2 = display.newImage("my_box.png")
box2.x = display.contentWidth/2
box2.y = display.contentWidth/2
box2: scale(.285,.285)
btnclick2 = display.newImage("limebox.png")
btnclick2: scale(.85,.85)
btnclick2.x = display.contentWidth/2
btnclick2.y = display.contentHeight/3
btnclick2.id = 2

box3 = display.newImage("my_box.png")
box3.x = display.contentWidth/1.25
box3.y = display.contentWidth/2
box3: scale(.285,.285)
btnclick3 = display.newImage("greenbox.png")
btnclick3: scale(.85,.85)
btnclick3.x = display.contentWidth/1.25
btnclick3.y = display.contentHeight/3
btnclick3.id = 3

-->Adds Boxes - row 2
box4 = display.newImage("my_box.png")
box4.x = display.contentWidth/5
box4.y = display.contentWidth/1.25
box4: scale(.285,.285)
btnclick4 = display.newImage("yellowbox.png")
btnclick4: scale(.85,.85)
btnclick4.x = display.contentWidth/5
btnclick4.y = display.contentHeight/1.875
btnclick4.id = 4

box5 = display.newImage("my_box.png")
box5.x = display.contentWidth/2
box5.y = display.contentWidth/1.25
box5: scale(.285,.285)
btnclick5 = display.newImage("orangebox.png")
btnclick5: scale(.85,.85)
btnclick5.x = display.contentWidth/2
btnclick5.y = display.contentHeight/1.875
btnclick5.id = 5

box6 = display.newImage("my_box.png")
box6.x = display.contentWidth/1.25
box6.y = display.contentWidth/1.25
box6: scale(.285,.285)
btnclick6 = display.newImage("purplebox.png")
btnclick6: scale(.85,.85)
btnclick6.x = display.contentWidth/1.25
btnclick6.y = display.contentHeight/1.875
btnclick6.id = 6

-->Adds Boxes - row 3
box7 = display.newImage("my_box.png")
box7.x = display.contentWidth/5
box7.y = display.contentWidth/.91
box7: scale(.285,.285)
btnclick7 = display.newImage("brownbox.png")
btnclick7: scale(.85,.85)
btnclick7.x = display.contentWidth/5
btnclick7.y = display.contentHeight/1.365
btnclick7.id = 7

box8 = display.newImage("my_box.png")
box8.x = display.contentWidth/2
box8.y = display.contentWidth/.91
box8: scale(.285,.285)
btnclick8 = display.newImage("redbox.png")
btnclick8: scale(.85,.85)
btnclick8.x = display.contentWidth/2
btnclick8.y = display.contentHeight/1.365
btnclick8.id = 8

box9 = display.newImage("my_box.png")
box9.x = display.contentWidth/1.25
box9.y = display.contentWidth/.91
box9: scale(.285,.285)
btnclick9 = display.newImage("graybox.png")
btnclick9: scale(.85,.85)
btnclick9.x = display.contentWidth/1.25
btnclick9.y = display.contentHeight/1.365
btnclick9.id = 9

pat = {btnclick1,btnclick2,btnclick3,btnclick4,btnclick5,btnclick6,btnclick7,btnclick8,btnclick9}
end


setup()


local gameoverText


function removings ()

scoreText:removeSelf()

end


endgame = function()


gameOver = true
   
   gameoverText = display.newText("GAMEOVER",0, 0, native.systemFont, 45)
   gameoverText.x = display.contentWidth/2
         gameoverText.y = display.contentHeight/11
         gameoverText:setTextColor(19, 117, 156) 
   transition.to(gameoverText, {alpha = 0, delay = 1000, time = 1000, onComplete=removings}) 
   restartButton = display.newText("RESTART", 0, 0, native.systemFont, 35)
    restartButton.x = display.contentWidth/2
         restartButton.y = display.contentHeight/5.45
         restartButton:setTextColor(255,110,110)

   scoreText = display.newText("Score: "..round-1, 0, 0, native.systemFont, 50)
   scoreText.x = display.contentWidth/2
   scoreText.y = display.contentHeight/1.1
   scoreText:setTextColor(219, 238, 234)
   transition.to(scoreText, {alpha = 0, delay = 1000, time = 1000, onComplete=removings}) 


   restartButton:addEventListener("tap", reset)
   btnclick1:removeEventListener("tap", patternIndex)
   btnclick2:removeEventListener("tap", patternIndex)
   btnclick3:removeEventListener("tap", patternIndex)
   btnclick4:removeEventListener("tap", patternIndex)
   btnclick5:removeEventListener("tap", patternIndex)
   btnclick6:removeEventListener("tap", patternIndex)
   btnclick7:removeEventListener("tap", patternIndex)
   btnclick8:removeEventListener("tap", patternIndex)
   btnclick9:removeEventListener("tap", patternIndex)
end


patternIndex = function (event)

 if (checker < round) then
  --if what you clicked is true
  if (event.target.id==pattern[checker+1] and gameOver == false) then
   light(pat[pattern[checker+1]], true)
   checker = checker + 1
   audio1Channel = audio.play( pop2 )

  else
     
   endgame()


   
  end

 end

end

local textStarter
local function removeText()

 textStarter:removeSelf();

end

local function endInput()

 if(checker == round) then

  btnclick1:removeEventListener("tap", patternIndex)
  btnclick2:removeEventListener("tap", patternIndex)
  btnclick3:removeEventListener("tap", patternIndex)
  btnclick4:removeEventListener("tap", patternIndex)
  btnclick5:removeEventListener("tap", patternIndex)
  btnclick6:removeEventListener("tap", patternIndex)
  btnclick7:removeEventListener("tap", patternIndex)
  btnclick8:removeEventListener("tap", patternIndex)
  btnclick9:removeEventListener("tap", patternIndex)


  textStarter= display.newText(tostring(round).." Correct!", 0, 0, native.systemFont, 50)
  textStarter.x = display.contentWidth/2
        textStarter.y = display.contentHeight/7
        textStarter:setTextColor(19, 117, 156)
  transition.to(textStarter, { size = 65, time = 1000, alpha = 0.0, onComplete=removeText})

  i = 0;
  round = round + 1;
  timer.performWithDelay(800,go)
  checker = 0;
  rate = rate * 1.01
 end

end



light = function (obj, once)

 if (once == false and i < round and gameOver == false) then
  transition.to(obj, {time=200, alpha = 0.1})
  transition.to(obj, {time=200, delay = 250, alpha = 5.0, onComplete=go})
 else
  transition.to(obj, {time=100, alpha = 0.1})
  transition.to(obj, {time=100, delay = 100, alpha = 5.0, onComplete=endInput})
 end
end

go = function()
 if (gameOver == false) then

  if (i == 0) then
   audio1Channel = audio.play( pop1 )
   pattern[#pattern+1] = math.random(1,9);
  end

  if (i < round) then
   audio1Channel = audio.play( pop1 )
   next = pattern[i+1];

   light(pat[next], false);
   i = i + 1;
  else


  
   btnclick1:addEventListener("tap", patternIndex)
   btnclick2:addEventListener("tap", patternIndex)
   btnclick3:addEventListener("tap", patternIndex)
   btnclick4:addEventListener("tap", patternIndex)
   btnclick5:addEventListener("tap", patternIndex)
   btnclick6:addEventListener("tap", patternIndex)
   btnclick7:addEventListener("tap", patternIndex)
   btnclick8:addEventListener("tap", patternIndex)
   btnclick9:addEventListener("tap", patternIndex)

  end
 end
end

local function start(event)
  gameOver = false
  textStart:removeSelf()
  timer.performWithDelay(1000,go)
  audio1Channel = audio.play( pop )
end

textStart= display.newImage("startbtn.png")
textStart.x = display.contentWidth/2
textStart.y = display.contentWidth/5
textStart:scale(.23, .23)


textStart:addEventListener("tap", start)

x = 0
y = 0

local function addHead()
end

updown = 0;
leftright=1;
rate = 2




 
