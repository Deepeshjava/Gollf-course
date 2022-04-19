/************************************************************
    /\ /\   |  |\  |  |      |``\ |  | ``|`` ``|``
   |  |  |  |  | \ |  |      |__/ |  |   |     |
   |  |  |  |  |  \|  |      |    \__/   |     |
   
         ___
        /   \                     |\\\\\\
        \   /                     |//////
         /|\                      |
        / | \                     |
        | | |                     |
        \/ \/                     |
        |\|/|                     |
        | | |                     |
        | D |               O    (_)
************************************************************/
frameRate(40);
var ballPOSx = 200;
var ballPOSy = 200;
var drop = false;
var Level1 = false;
var Level2 = false;
var Level3 = false;
var Level4 = false;
var Level5 = false;
var Level6 = false;
var Level7 = false;
var Level8 = false;
var Level9 = false;
var Level10 = false;
var Level11 = false;
var Level12 = false;
var Level13 = false;
var Level14 = false;
var Level15 = false;
var Level16 = false;
var Level17 = false;
var Level18 = false;
var LevelStart = true;
var titleScreen = true;
var power = 0;
var powerX = 0;
var powerY = 0;
var shotLEFT = false;
var shotUP = false;
var shot = false;
var endClick = true;
var dotx = 0;
var doty = 0;
var speedX = 0;
var speedY = 0;
var shotCount = 0;
var shotDiminish = 0;
var resetShot = false;
var holePOSx = 300;
var holePOSy = 200;
var dX1 = 75;
var dX2 = 115;
var dY1 = 165;
var dY2 = 235;
var eX = 100;
var eY = 320;
var oldX = 0;
var oldY = 0;
var L1S = 0;
var L2S = 0;
var L3S = 0;
var L4S = 0;
var L5S = 0;
var L6S = 0;
var L7S = 0;
var L8S = 0;
var L9S = 0;
var L10S = 0;
var L11S = 0;
var L12S = 0;
var L13S = 0;
var L14S = 0;
var L15S = 0;
var L16S = 0;
var L17S = 0;
var L18S = 0;
var LevelSelect = 0;
var ScoreDisplay = false;
var dY = 0;
var restart = 0;
var linePOS = 0;
var lineUP = false;
var grav = 1;
var slopeX = false;
var slopeY = false;
var textDiminish = 255;
var textDiminishB = 0;
var underGround = false;
var water = false;
var underWater = false;
var waterTime = 0;
var tips = false;
var PrevSlopeX = 0;
var PrevSlopeY = 0;
var PrevSpeedX = 0;
var PrevSpeedY = 0;
var alertText = "";
var AutoComplete = false;
var AConoff = false;
var slopeLEFT = false;
var slopeRIGHT = false;
var slopeUP = false;
var slopeDOWN = false;
var bunker = false;
var UsedCommands = false;
var delayTimer = 0;
var selection = 0;
var Bonus = 0;
var LevelMenu = false;
var a = 0;
var b = 0;
var c = 0;
var roll = 5;
var tS = 7;
var onoffString = "OFF";
var tipSelect = 0;
var tY = 0;
var tipDisplay = false;
var endGame = false;


var keys = [];
var keyPressed = function(){keys[keyCode] = true;};
var keyReleased = function(){keys[keyCode] = false;};

var draw = function() {
    background(107, 72, 1);
    
    var LS = [L1S, L2S, L3S, L4S, L5S, L6S, L7S, L8S, L9S, L10S, L11S, L12S, L13S, L14S, L15S, L16S, L17S, L18S];
    var Par = [2, 3, 3, 3, 2, 2, 5, 2, 3, 3, 3, 3, 3, 3, 2, 4, 2, 2];
    var ParSum = [2, 5, 8, 11, 13, 15, 20, 22, 25, 28, 31, 34, 37, 40, 42, 46, 48, 50];
    var LST = L1S + L2S + L3S + L4S + L5S + L6S + L7S + L8S + L9S + L10S + L11S + L12S + L13S + L14S + L15S + L16S + L17S + L18S;
    if (speedX <= 0.1 && speedY <= 0.1) {
        resetShot = true;
        speedX = 0;
        speedY = 0;
        if (shot && mouseIsPressed && !endClick && !titleScreen && !endGame) {
            speedX = powerX/4;
            speedY = powerY/4;
            shotDiminish = power/5 ;
            shotCount += 1;
            if (Level1) {L1S += 1;}
            if (Level2) {L2S += 1;}
            if (Level3) {L3S += 1;}
            if (Level4) {L4S += 1;}
            if (Level5) {L5S += 1;}
            if (Level6) {L6S += 1;}
            if (Level7) {L7S += 1;}
            if (Level8) {L8S += 1;}
            if (Level9) {L9S += 1;}
            if (Level10) {L10S += 1;}
            if (Level11) {L11S += 1;}
            if (Level12) {L12S += 1;}
            if (Level13) {L13S += 1;}
            if (Level14) {L14S += 1;}
            if (Level15) {L15S += 1;}
            if (Level16) {L16S += 1;}
            if (Level17) {L17S += 1;}
            if (Level18) {L18S += 1;}
            endClick = true;
        }
        shot = false;
    } else {
        resetShot = false;
        if (shotLEFT) {
            ballPOSx -= speedX;
        } else {
            ballPOSx += speedX;
        }
        if (shotUP) {
            ballPOSy -= speedY;
        } else {
            ballPOSy += speedY;
        }
        if (speedX > 0 && !slopeY){
        speedX -= speedX/shotDiminish;
        } else {
            if (!slopeY){
                speedX = 0;
            } else {
                speedX -= speedX/(shotDiminish * 1.5);
            }
        }
        if (speedY > 0 && !slopeX) {
        speedY -= speedY/shotDiminish;
        } else {
            if (!slopeX) {
                speedY = 0;
            } else {
                speedY -= speedY/(shotDiminish * 1.5);
            }
        }
    }
    power = dist(mouseX, mouseY, ballPOSx, ballPOSy);
    powerX = dist(mouseX, 0, ballPOSx, 0);
    powerY = dist(0, mouseY, 0, ballPOSy);
    
    slopeX = false;
    slopeY = false;
    slopeLEFT = false;
    slopeRIGHT = false;
    slopeUP = false;
    slopeDOWN = false;
    water = false;
    bunker = false;
    
    //LEVEL 1
    if (Level1) {
        fill(30, 168, 2);
        strokeWeight(5);
        stroke(173, 116, 2);
        rect(50, 100, 300, 200);
        noStroke();
        fill(0, 0, 0, 100);
        rect(75, 165, 40, 70);
        strokeWeight(1);
        dX1 = 75;
        dX2 = 115;
        dY1 = 165;
        dY2 = 235;
        holePOSx = 300;
        holePOSy = 200;
        if (tips) {
        if (textDiminish > 0) {
            if (drop) {
                textDiminish -= 0.2;
            } else {
                textDiminish -= 5;
            }
        }
        textSize(11);
        fill(255, 255, 0, textDiminish);
        text("Click to drop your ball in the dark green zone, then click again to putt it.", 35, 90);
        text("The farther back you hold the putter, the harder the putt.", 65, 320);
        }
        //Boundaries
    if (ballPOSy >= 295) {
        ballPOSy = 295;
        shotUP = true;
    }
    if (ballPOSx >= 345) {
        ballPOSx = 345;
        shotLEFT = true;
    }
    if (ballPOSy <= 106) {
        ballPOSy = 106;
        shotUP = false;
    }
    if (ballPOSx <= 56) {
        ballPOSx = 56;
        shotLEFT = false;
    }
    }
    
    //LEVEL 2
    if (Level2) {
        fill(30, 168, 2);
        strokeWeight(5);
        stroke(173, 116, 2);
        rect(100, 80, 200, 300);
        fill(92, 62, 1);
        rect(175, 80, 10, 225);
        rect(215, 80, 10, 225);
        noStroke();
        fill(0, 0, 0, 100);
        rect(110, 90, 55, 40);
        dX1 = 110;
        dX2 = 165;
        dY1 = 90;
        dY2 = 130;
        holePOSx = 263;
        holePOSy = 100;
        strokeWeight(1);
        if (tips) {
        if (textDiminish > 0) {
            if (drop) {
                textDiminish -= 0.2;
            } else {
                textDiminish -= 5;
            }
        }
        textSize(11);
        fill(255, 255, 0, textDiminish);
        text("Make your way around obstacles to get to the hole.", 77, 70);
        text("<--- Restart Hole", 40, 30);
        }
        //Boundaries
    if (ballPOSy >= 375) {
        ballPOSy = 375;
        shotUP = true;
    }
    if (ballPOSx >= 295) {
        ballPOSx = 295;
        shotLEFT = true;
    }
    if (ballPOSy <= 86) {
        ballPOSy = 86;
        shotUP = false;
    }
    if (ballPOSx <= 106) {
        ballPOSx = 106;
        shotLEFT = false;
    }
    if (ballPOSy <= 305) {
    if (oldX < 170 && ballPOSx >= 170) {
        shotLEFT = true;
        oldX = 169;
        ballPOSx = 169;
    }
    if (oldX > 190 && ballPOSx <= 190) {
        shotLEFT = false;
        oldX = 191;
        ballPOSx = 191;
    }
    if (oldX < 210 && ballPOSx >= 210) {
        shotLEFT = true;
        oldX = 209;
        ballPOSx = 209;
    }
    if (oldX > 231 && ballPOSx <= 231) {
        shotLEFT = false;
        oldX = 232;
        ballPOSx = 232;
    }
    }
    if (ballPOSy <= 313 && oldY < 313) {
    if (ballPOSx >= 170 && ballPOSx <= 190) {
        ballPOSy = 313;
        shotUP = false;
    }
    if (ballPOSx >= 210 && ballPOSx <= 231) {
        ballPOSy = 313;
        shotUP = false;
    }
    }
    }
    
    //LEVEL 3
    if (Level3) {
        fill(30, 168, 2);
        strokeWeight(5);
        stroke(173, 116, 2);
        rect(100, 50, 200, 300);
        fill(128, 86, 2);
        rect(100, 50, 70, 50);
        rect(230, 50, 70, 50);
        strokeWeight(6);
        stroke(110);
        line(160, 290, 240, 290);
        line(105, 230, 145, 230);
        line(255, 230, 295, 230);
        line(160, 170, 240, 170);
        noStroke();
        fill(0, 0, 0, 100);
        rect(160, 300, 80, 40);
        strokeWeight(1);
        holePOSx = 200;
        holePOSy = 79;
        dX1 = 160;
        dX2 = 240;
        dY1 = 300;
        dY2 = 340;
        if (tips) {
        if (textDiminish > 0) {
            if (drop) {
                textDiminish -= 0.2;
            } else {
                textDiminish -= 5;
            }
        }
        textSize(11);
        fill(255, 255, 0, textDiminish);
        text("The faster your ball is going the more accurate you have to be to get it in the hole.", 5, 45);
        text("If it is going too fast it can't go in the hole at all", 88, 370);
        }
        //Boundaries
    if (ballPOSy >= 345) {
        ballPOSy = 345;
        shotUP = true;
    }
    if (ballPOSx >= 295) {
        ballPOSx = 295;
        shotLEFT = true;
    }
    if (ballPOSy <= 56) {
        ballPOSy = 56;
        shotUP = false;
    }
    if (ballPOSx <= 106) {
        ballPOSx = 106;
        shotLEFT = false;
    }
    if (ballPOSx >= 158 && ballPOSx <= 243) {
        if (oldY > 296 && ballPOSy <= 296) {
            oldY = 297;
            ballPOSy = 297;
            shotUP = false;
        }
        if (oldY < 285 && ballPOSy >= 285) {
            oldY = 284;
            ballPOSy = 284;
            shotUP = true;
        }
        if (oldY > 176 && ballPOSy <= 176) {
            oldY = 177;
            ballPOSy = 177;
            shotUP = false;
        }
        if (oldY < 165 && ballPOSy >= 165) {
            oldY = 164;
            ballPOSy = 164;
            shotUP = true;
        }
    }
    if (ballPOSx <= 148) {
        if (oldY > 236 && ballPOSy <= 236) {
            oldY = 237;
            ballPOSy = 237;
            shotUP = false;
        }
        if (oldY < 225 && ballPOSy >= 225) {
            oldY = 224;
            ballPOSy = 224;
            shotUP = true;
        }
    }
    if (ballPOSx >= 253) {
        if (oldY > 236 && ballPOSy <= 236) {
            oldY = 237;
            ballPOSy = 237;
            shotUP = false;
        }
        if (oldY < 225 && ballPOSy >= 225) {
            oldY = 224;
            ballPOSy = 224;
            shotUP = true;
        }
    }
    if (ballPOSy <= 106 && oldY > 106) {
        if (ballPOSx <= 176) {
            ballPOSy = 107;
            shotUP = false;
        }
        if (ballPOSx >= 228) {
            ballPOSy = 107;
            shotUP = false;
        }
    }
    if (ballPOSy <= 103) {
        if (ballPOSx <= 176 && oldX > 176) {
            ballPOSx = 176;
            shotLEFT = false;
        }
        if (ballPOSx >= 228 && oldX < 228) {
            ballPOSx = 228;
            shotLEFT = true;
        }
    }
    }
    
    //LEVEL 4
    if (Level4) {
        fill(30, 168, 2);
        strokeWeight(5);
        stroke(173, 116, 2);
        rect(30, 110, 340, 210);
        fill(128, 86, 2);
        rect(30, 250, 70, 70);
        line(30, 250, 270, 250);
        line(110, 180, 370, 180);
        noStroke();
        fill(0, 0, 0, 100);
        rect(105, 255, 40, 61);
        strokeWeight(1);
        dX1 = 105;
        dX2 = 145;
        dY1 = 255;
        dY2 = 316;
        holePOSx = 345;
        holePOSy = 145;
        if (tips) {
        if (textDiminish > 0) {
            if (drop) {
                textDiminish -= 0.2;
            } else {
                textDiminish -= 5;
            }
        }
        textSize(11);
        fill(255, 255, 0, textDiminish);
        text("Put your mouse over the tab at the top to see your score card", 50, 105);
        text("^SCORE CARD^", 161, 20);
        }
        //Boundaries
    if (ballPOSy >= 315) {
        ballPOSy = 315;
        shotUP = true;
    }
    if (ballPOSx >= 365) {
        ballPOSx = 365;
        shotLEFT = true;
    }
    if (ballPOSy <= 116) {
        ballPOSy = 116;
        shotUP = false;
    }
    if (ballPOSx <= 36) {
        ballPOSx = 36;
        shotLEFT = false;
    }
    if (ballPOSy >= 250 && ballPOSx <= 106 && oldY > 250) {
        ballPOSx = 106;
        shotLEFT = false;
    }
    if (ballPOSx <= 273) {
        if (oldY > 256 && ballPOSy <= 256) {
            oldY = 257;
            ballPOSy = 257;
            shotUP = false;
        }
        if (oldY < 245 && ballPOSy >= 245) {
            oldY = 244;
            ballPOSy = 244;
            shotUP = true;
        }
    }
    if (ballPOSx >= 107) {
        if (oldY > 186 && ballPOSy <= 186) {
            oldY = 187;
            ballPOSy = 187;
            shotUP = false;
        }
        if (oldY < 175 && ballPOSy >= 175) {
            oldY = 174;
            ballPOSy = 174;
            shotUP = true;
        }
    }
    }
    
    //LEVEL 5
    if (Level5) {
        fill(30, 168, 2);
        strokeWeight(5);
        stroke(173, 116, 2);
        rect(50, 120, 300, 160);
        dX1 = 75;
        dX2 = 115;
        dY1 = 165;
        dY2 = 235;
        holePOSx = 300;
        holePOSy = 200;
        if (linePOS <= 4) {
            lineUP = false;
        }
        if (linePOS >= 75) {
            lineUP = true;
        }
        if (lineUP) {
            linePOS -= 1;
        } else {
            linePOS += 1;
        }
        strokeWeight(6);
        stroke(100);
        line(150, linePOS + 120, 150, linePOS + 200);
        line(200, 280 - linePOS, 200, 200 - linePOS);
        line(250, linePOS + 120, 250, linePOS + 200);
        noStroke();
        fill(0, 0, 0, 100);
        rect(75, 165, 40, 70);
        strokeWeight(1);
        if (tips) {
        if (textDiminish > 0) {
            if (drop) {
                textDiminish -= 0.2;
            } else {
                textDiminish -= 5;
            }
        }
        textSize(11);
        fill(255, 255, 0, textDiminish);
        text("Some obstacles may move, aim accordingly.", 95, 105);
        }
        //Boundaries
    if (ballPOSy >= 275) {
        ballPOSy = 275;
        shotUP = true;
    }
    if (ballPOSx >= 345) {
        ballPOSx = 345;
        shotLEFT = true;
    }
    if (ballPOSy <= 126) {
        ballPOSy = 126;
        shotUP = false;
    }
    if (ballPOSx <= 56) {
        ballPOSx = 56;
        shotLEFT = false;
    }
    if (ballPOSy >= linePOS + 117 && ballPOSy <= linePOS + 203) {
        if (oldX < 144 && ballPOSx >= 144) {
            oldX = 143;
            ballPOSx = 143;
            shotLEFT = true;
        }
        if (oldX > 156 && ballPOSx <= 156) {
            oldX = 157;
            ballPOSx = 157;
            shotLEFT = false;
        }
        if (oldX < 244 && ballPOSx >= 244) {
            oldX = 243;
            ballPOSx = 243;
            shotLEFT = true;
        }
        if (oldX > 256 && ballPOSx <= 256) {
            oldX = 257;
            ballPOSx = 257;
            shotLEFT = false;
        }
    }
    if (ballPOSy >= 207 - linePOS && ballPOSy <= 283 - linePOS) {
        if (oldX < 194 && ballPOSx >= 194) {
            oldX = 193;
            ballPOSx = 193;
            shotLEFT = true;
        }
        if (oldX > 206 && ballPOSx <= 206) {
            oldX = 207;
            ballPOSx = 207;
            shotLEFT = false;
        }
    } 
    }
    
    //LEVEL 6
    if (Level6) {
        fill(30, 168, 2);
        strokeWeight(5);
        stroke(173, 116, 2);
        rect(50, 100, 300, 200);
        stroke(153, 103, 3);
        line(200, 105, 200, 190);
        line(200, 295, 200, 210);
        line(175, 190, 225, 190);
        line(175, 210, 225, 210);
        stroke(100);
        line(170, 131 + linePOS, 170, 189 + linePOS);
        line(230, 209 - linePOS, 230, 271 - linePOS);
        line(310, 191, 310, 208);
        noStroke();
        fill(0, 0, 0, 100);
        rect(75, 165, 40, 70);
        strokeWeight(1);
        if (linePOS <= 0) {
            lineUP = false;
        }
        if (linePOS >= 80) {
            lineUP = true;
        }
        if (lineUP) {
            linePOS -= 1.5;
        } else {
            linePOS += 1.5;
        }
        //Boundaries
    if (ballPOSy >= 295) {
        ballPOSy = 295;
        shotUP = true;
    }
    if (ballPOSx >= 345) {
        ballPOSx = 345;
        shotLEFT = true;
    }
    if (ballPOSy <= 106) {
        ballPOSy = 106;
        shotUP = false;
    }
    if (ballPOSx <= 56) {
        ballPOSx = 56;
        shotLEFT = false;
    }
    if (ballPOSy >= 209 - linePOS && ballPOSy <= 271 - linePOS) {
        if (oldX < 225 && ballPOSx >= 225) {
            oldX = 224;
            ballPOSx = 224;
            shotLEFT = true;
        }
        if (oldX > 236 && ballPOSx <= 236) {
            oldX = 237;
            ballPOSx = 237;
            shotLEFT = false;
        }
    }
    if (ballPOSy >= 129 + linePOS && ballPOSy <= 192 + linePOS) {
        if (oldX < 165 && ballPOSx >= 165) {
            oldX = 164;
            ballPOSx = 164;
            shotLEFT = true;
        }
        if (oldX > 176 && ballPOSx <= 176) {
            oldX = 177;
            ballPOSx = 177;
            shotLEFT = false;
        }
    }
    if (ballPOSx >= 170 && ballPOSx <= 230) {
        if (oldY > 216 && ballPOSy <= 216) {
            oldY = 217;
            ballPOSy = 217;
            shotUP = false;
        }
        if (oldY < 205 && ballPOSy >= 205) {
            oldY = 204;
            ballPOSy = 204;
            shotUP = true;
        }
        if (oldY > 196 && ballPOSy <= 196) {
            oldY = 197;
            ballPOSy = 197;
            shotUP = false;
        }
        if (oldY < 185 && ballPOSy >= 185) {
            oldY = 184;
            ballPOSy = 184;
            shotUP = true;
        }
    }
    if (oldX < 195 && ballPOSx >= 195) {
        if (ballPOSy < 190) {
            oldX = 194;
            ballPOSx = 194;
            shotLEFT = true;
        }
        if (ballPOSy > 210) {
            oldX = 194;
            ballPOSx = 194;
            shotLEFT = true;
        }
    }
    if (oldX > 206 && ballPOSx <= 206) {
        if (ballPOSy < 190) {
            oldX = 207;
            ballPOSx = 207;
            shotLEFT = false;
        }
        if (ballPOSy > 210) {
            oldX = 207;
            ballPOSx = 207;
            shotLEFT = false;
        }
    }
    if (ballPOSy >= 189 && ballPOSy <= 211) {
        if (oldX < 305 && ballPOSx >= 305) {
            oldX = 304;
            ballPOSx = 304;
            shotLEFT = true;
        }
        if (oldX > 316 && ballPOSx <= 316) {
            oldX = 317;
            ballPOSx = 317;
            shotLEFT = false;
        }
    }
    }
    
    //LEVEL 7
    if (Level7) {
        fill(30, 168, 2);
        strokeWeight(5);
        stroke(173, 116, 2);
        rect(30, 110, 340, 210);
        fill(128, 86, 2);
        line(30, 180, 280, 180);
        line(220, 250, 350, 250);
        line(220, 250, 220, 230);
        line(220, 180, 220, 200);
        line(110, 225, 220, 225);
        line(90, 205, 220, 205);
        line(110, 225, 110, 300);
        line(90, 205, 90, 300);
        line(50, 300, 90, 300);
        line(50, 235, 50, 300);
        line(50, 235, 60, 235);
        line(60, 235, 60, 205);
        line(30, 205, 60, 205);
        line(110, 300, 350, 300);
        line(350, 300, 350, 250);
        noStroke();
        rect(113, 253, 235, 45);
        rect(113, 228, 105, 25);
        rect(63, 183, 25, 115);
        rect(33, 183, 185, 20);
        rect(53, 238, 25, 60);
        fill(0, 0, 0, 100);
        rect(35, 115, 80, 61);
        dX1 = 35;
        dX2 = 115;
        dY1 = 115;
        dY2 = 176;
        holePOSx = 45;
        holePOSy = 220;
        strokeWeight(1);
        if (tips) {
        if (textDiminish > 0) {
            if (drop) {
                textDiminish -= 0.2;
            } else {
                textDiminish -= 5;
            }
        }
        textSize(11);
        fill(255, 255, 0, textDiminish);
        text("There are some bugs in this hole, sorry.", 105, 340);
        }
        //Boundaries
    if (ballPOSy >= 315) {
        ballPOSy = 315;
        shotUP = true;
    }
    if (ballPOSx >= 365) {
        ballPOSx = 365;
        shotLEFT = true;
    }
    if (ballPOSy <= 116) {
        ballPOSy = 116;
        shotUP = false;
    }
    if (ballPOSx <= 36) {
        ballPOSx = 36;
        shotLEFT = false;
    }
    if (ballPOSx <= 282) {
        if (oldY < 175 && ballPOSy >= 175) {
            oldY = 174;
            ballPOSy = 174;
            shotUP = true;
        }
        if (oldY > 186 && ballPOSy <= 186) {
            oldY = 187;
            ballPOSy = 187;
            shotUP = false;
        }
    }
    if (ballPOSx <= 226) {
        if (oldX > 226) {
            if (ballPOSy >= 180 && ballPOSy < 205) {
                oldX = 226;
                ballPOSx = 226;
                shotLEFT = false;
            }
            if (ballPOSy >= 225 && ballPOSy <= 250) {
                oldX = 226;
                ballPOSx = 226;
                shotLEFT = false;
            }
        }
        if (oldY > 211 && ballPOSy <= 211) {
            oldY = 212;
            ballPOSy = 212;
            shotUP = false;
        }
    }
    if (ballPOSx >= 105) {
        if (ballPOSy >= 223 && ballPOSy <= 303) {
            if (oldX < 105) {
                oldX = 104;
                ballPOSx = 104;
                shotLEFT = true;
            }
            if (ballPOSy >= 250 && oldX > 356 && ballPOSx <= 356) {
                oldX = 356;
                ballPOSx = 356;
                shotLEFT = false;
            }
        }
    }
    if (ballPOSx >= 105 && ballPOSx <= 356 && oldY > 306 && ballPOSy <= 306) {
        oldY = 307;
        ballPOSy = 307;
        shotUP = false;
    }
    if (ballPOSx >= 110 && ballPOSx <= 226 && oldY < 220 && ballPOSy >= 220) {
        oldY = 219;
        ballPOSy = 219;
        shotUP = true;
    }
    if (ballPOSx >= 220 && ballPOSx <= 350 && oldY < 245 && ballPOSy >= 245) {
        oldY = 244;
        ballPOSy = 244;
        shotUP = true;
    }
    if (ballPOSy >= 200 && ballPOSy <= 306 && oldX > 96 && ballPOSx <= 96) {
        oldX = 97;
        ballPOSx = 97;
        shotLEFT = false;
    }
    if (ballPOSx >= 45 && ballPOSx <= 96 && oldY > 306 && ballPOSy <= 306) {
        oldX = 307;
        ballPOSy = 307;
        shotUP = false;
    }
    if (ballPOSy >= 230 && ballPOSy <= 306 && oldX < 45 && ballPOSx >= 45) {
        oldX = 44;
        ballPOSx = 44;
        shotLEFT = true;
    }
    if (ballPOSy > 200 && ballPOSy <= 235 && oldX < 55 && ballPOSx >= 55) {
        oldX = 54;
        ballPOSx = 54;
        shotLEFT = true;
    }
    if (ballPOSx >= 45 && ballPOSx <= 65 && oldY < 230 && ballPOSy >= 230) {
        oldY = 229;
        ballPOSy = 229;
        shotUP = true;
    }
    }
    
    //LEVEL 8
    if (Level8) {
        fill(30, 168, 2);
        strokeWeight(5);
        stroke(173, 116, 2);
        rect(50, 100, 300, 200);
        noStroke();
        fill(0, 0, 0, 100);
        rect(75, 165, 40, 70);
        strokeWeight(1);
        fill(3, 148, 8);
        rect(150, 103, 80, 195);
        fill(13, 184, 4);
        rect(270, 103, 63, 195);
        for (var aRep = 0; aRep < 10; aRep += 1) {
            stroke(0, 125, 0);
            line(155, 110 + aRep * 20, 225, 105 + aRep * 20);
            line(155, 110 + aRep * 20, 225, 115 + aRep * 20);
            stroke(90, 190, 90);
            line(328, 110 + aRep * 20, 275, 105 + aRep * 20);
            line(328, 110 + aRep * 20, 275, 115 + aRep * 20);
        }
        noStroke();
        dX1 = 75;
        dX2 = 115;
        dY1 = 165;
        dY2 = 235;
        holePOSx = 250;
        holePOSy = 120;
        if (tips) {
        if (textDiminish > 0) {
            if (drop) {
                textDiminish -= 0.2;
            } else {
                textDiminish -= 5;
            }
        }
        textSize(11);
        fill(255, 255, 0, textDiminish);
        text("This hole introduces slopes. The arrows point to the bottom\nwhile the large end is at the top.", 52, 80);
        stroke(255, 255, 0, textDiminish);
        strokeWeight(3);
        line(50, 350, 150, 350);
        line(150, 350, 230, 325);
        line(230, 325, 270, 325);
        line(270, 325, 333, 350);
        line(333, 350, 350, 350);
        text("<SIDE VIEW", 300, 370);
        }
        //Boundaries
    if (ballPOSy >= 295) {
        ballPOSy = 295;
        shotUP = true;
    }
    if (ballPOSx >= 345) {
        ballPOSx = 345;
        shotLEFT = true;
    }
    if (ballPOSy <= 106) {
        ballPOSy = 106;
        shotUP = false;
    }
    if (ballPOSx <= 56) {
        ballPOSx = 56;
        shotLEFT = false;
    }
    if (ballPOSx > 150 && ballPOSx < 230) {
        slopeLEFT = true;
    }
    if (ballPOSx > 270 && ballPOSx < 335) {
        slopeRIGHT = true;
    }
    }
    
    //LEVEL 9
    if (Level9) {
        fill(30, 168, 2);
        strokeWeight(5);
        stroke(173, 116, 2);
        rect(35, 100, 330, 250);
        line(35, 290, 291, 290);
        noStroke();
        fill(0, 0, 0, 100);
        rect(41, 145, 40, 100);
        dX1 = 41;
        dX2 = 81;
        dY1 = 145;
        dY2 = 245;
        holePOSx = 65;
        holePOSy = 320;
        strokeWeight(1);
        fill(3, 148, 8);
        rect(85, 168, 70, 120);
        rect(155, 228, 70, 60);
        rect(225, 168, 70, 120);
        fill(13, 184, 4);
        rect(85, 103, 70, 60);
        rect(155, 103, 70, 120);
        rect(225, 103, 70, 60);
        rect(295, 103, 68, 190);
        for (var aRep = 0; aRep < 3; aRep += 1) {
            stroke(90, 190, 90);
            line(95 + aRep * 20, 110, 100 + aRep * 20, 157);
            line(105 + aRep * 20, 110, 100 + aRep * 20, 157);
            line(165 + aRep * 20, 110, 170 + aRep * 20, 217);
            line(175 + aRep * 20, 110, 170 + aRep * 20, 217);
            line(235 + aRep * 20, 110, 240 + aRep * 20, 157);
            line(245 + aRep * 20, 110, 240 + aRep * 20, 157);
            line(305 + aRep * 20, 110, 310 + aRep * 20, 288);
            line(315 + aRep * 20, 110, 310 + aRep * 20, 288);
            stroke(0, 125, 0);
            line(95 + aRep * 20, 282, 100 + aRep * 20, 175);
            line(105 + aRep * 20, 282, 100 + aRep * 20, 175);
            line(165 + aRep * 20, 282, 170 + aRep * 20, 235);
            line(175 + aRep * 20, 282, 170 + aRep * 20, 235);
            line(235 + aRep * 20, 282, 240 + aRep * 20, 175);
            line(245 + aRep * 20, 282, 240 + aRep * 20, 175);
        }
        //Boundaries
    if (ballPOSy >= 345) {
        ballPOSy = 345;
        shotUP = true;
    }
    if (ballPOSx >= 360) {
        ballPOSx = 360;
        shotLEFT = true;
    }
    if (ballPOSy <= 106) {
        ballPOSy = 106;
        shotUP = false;
    }
    if (ballPOSx <= 41) {
        ballPOSx = 41;
        shotLEFT = false;
    }
    if (ballPOSx <= 294) {
        if (oldY < 285 && ballPOSy >= 285) {
            oldY = 284;
            ballPOSy = 284;
            shotUP = true;
        }
        if (oldY > 296 && ballPOSy <= 296) {
            oldY = 297;
            ballPOSy = 297;
            shotUP = false;
        }
    }
    if (ballPOSx >= 85 && ballPOSx <= 365 && ballPOSy < 163) {
        slopeDOWN = true;
    }
    if (ballPOSx >= 155 && ballPOSx <= 225 && ballPOSy < 223) {
        slopeDOWN = true;
    }
    if (ballPOSx >= 295 && ballPOSy < 293) {
        slopeDOWN = true;
    }
    if (ballPOSx >= 85 && ballPOSx <= 295 && ballPOSy > 228 && ballPOSy <= 288) {
        slopeUP = true;
    }
    if (ballPOSx >= 85 && ballPOSx <= 155 && ballPOSy > 168 && ballPOSy <= 288) {
        slopeUP = true;
    }
    if (ballPOSx >= 225 && ballPOSx <= 295 && ballPOSy > 168 && ballPOSy <= 288) {
        slopeUP = true;
    }
    }
    
    //LEVEL 10
    if (Level10) {
        fill(30, 168, 2);
        strokeWeight(5);
        stroke(173, 116, 2);
        rect(50, 80, 300, 260);
        line(50, 160, 160, 160);
        line(240, 160, 350, 160);
        fill(128, 86, 2);
        rect(140, 240, 20, 20);
        rect(240, 240, 20, 100);
        rect(115, 265, 20, 20);
        stroke(0, 158, 0);
        stroke(100);
        line(165, 160, 165, 258);
        line(235, 160, 235, 258);
        noStroke();
        fill(0, 0, 0, 100);
        rect(55, 85, 70, 71);
        rect(276, 85, 70, 71);
        strokeWeight(1);
        fill(3, 148, 8);
        rect(168, 157, 65, 30);
        fill(13, 184, 4);
        rect(168, 231, 65, 30);
        rect(120, 163, 43, 75);
        rect(263, 238, 85, 82);
        if (mouseX <= 125) {
            dX1 = 55;
        dX2 = 125;
        }
        if (mouseX >= 276) {
            dX1 = 276;
            dX2 = 346;
        }
        dY1 = 85;
        dY2 = 156;
        holePOSx = 305;
        holePOSy = 200;
        if (tips) {
        if (textDiminish > 0) {
            if (drop) {
                textDiminish -= 0.2;
            } else {
                textDiminish -= 5;
            }
        }
        textSize(11);
        fill(255, 255, 0, textDiminish);
        text("There are 2 drop zones in this hole; use which ever you like.", 50, 75);
        text("There's also a bridge. Go under it to get to the hole", 80, 360);
        }
        for (var bRep = 0; bRep < 3; bRep += 1) {
            stroke(0, 125, 0);
            line(175 + bRep * 20, 183, 180 + bRep * 20, 160);
            line(185 + bRep * 20, 183, 180 + bRep * 20, 160);
            stroke(90, 190, 90);
            line(175 + bRep * 20, 235, 180 + bRep * 20, 258);
            line(185 + bRep * 20, 235, 180 + bRep * 20, 258);
        }
        for (var cRep = 0; cRep < 4; cRep += 1) {
            stroke(90, 190, 90);
            line(269 + cRep * 20, 245, 274 + cRep * 20, 313);
            line(279 + cRep * 20, 245, 274 + cRep * 20, 313);
            line(125, 168 + cRep * 18, 156, 172 + cRep * 18);
            line(125, 176 + cRep * 18, 156, 172 + cRep * 18);
        }
        for (var aRep = 0; aRep < 10; aRep += 1) {
            stroke(0, 0, 0, 15 * aRep);
            line(153 + aRep, 163, 153 + aRep, 237);
            line(247 - aRep, 163, 247 - aRep, 237);
        }
        //Boundaries
    if (ballPOSy >= 335) {
        ballPOSy = 335;
        shotUP = true;
    }
    if (ballPOSx >= 345) {
        ballPOSx = 345;
        shotLEFT = true;
    }
    if (ballPOSy <= 86) {
        ballPOSy = 86;
        shotUP = false;
    }
    if (ballPOSx <= 56) {
        ballPOSx = 56;
        shotLEFT = false;
    }
    if (underGround && ballPOSy <= 160) {
        ballPOSy = 160;
        shotUP = false;
    }
    if (underGround && ballPOSy >= 240) {
        ballPOSy = 240;
        shotUP = true;
    }
    if (ballPOSx <= 163) {
        if (oldY < 155 && ballPOSy >= 155) {
            oldY = 154;
            ballPOSy = 154;
            shotUP = true;
        }
        if (oldY > 166 && ballPOSy <= 166) {
            oldY = 167;
            ballPOSy = 167;
            shotUP = false;
        }
    }
    if (ballPOSx >= 232) {
        if (oldY < 155 && ballPOSy >= 155) {
            oldY = 154;
            ballPOSy = 154;
            shotUP = true;
        }
        if (oldY > 166 && ballPOSy <= 166) {
            oldY = 167;
            ballPOSy = 167;
            shotUP = false;
        }
    }
    if (ballPOSy >= 158 && ballPOSy <= 261 && !underGround) {
        if (oldX < 160 && ballPOSx >= 160) {
            underGround = true;
        }
        if (oldX > 171 && ballPOSx <= 171) {
            oldX = 172;
            ballPOSx = 172;
            shotLEFT = false;
        }
        if (oldX < 230 && ballPOSx >= 230) {
            oldX = 229;
            ballPOSx = 229;
            shotLEFT = true;
        }
        if (oldX > 241 && ballPOSx <= 241) {
            underGround = true;
        }
    }
    if (ballPOSy >= 238 && ballPOSy <= 263 && oldX < 135 && ballPOSx >= 135) {
        oldX = 134;
        ballPOSx = 134;
         shotLEFT = true;
    }
    if (ballPOSx >= 138 && ballPOSx <= 163 && oldY < 235 && ballPOSy >= 235) {
        oldY = 234;
        ballPOSy = 234;
        shotUP = true;
    }
    if (ballPOSx >= 138 && ballPOSx <= 168 && oldY > 266 && ballPOSy <= 266) {
        oldY = 267;
        ballPOSy = 267;
        shotUP = false;
    }
    if (ballPOSy >= 238) {
        if (oldX < 235 && ballPOSx >= 235) {
            oldX = 234;
            ballPOSx = 234;
            shotLEFT = true;
        }
        if (oldX > 266 && ballPOSx <= 266) {
            oldX = 267;
            ballPOSx = 267;
            shotLEFT = false;
        }
    }
    if (ballPOSx >= 238 && ballPOSx <= 263 && oldY < 235 && ballPOSy >= 235) {
        oldY = 234;
        ballPOSy = 234;
        shotUP = true;
    }
    if (ballPOSy >= 263 && ballPOSy <= 288) {
        if (oldX < 110 && ballPOSx >= 110) {
            oldX = 109;
            ballPOSx = 109;
            shotLEFT = true;
        }
        if (oldX > 141 && ballPOSx <= 141) {
            oldX = 142;
            ballPOSx = 142;
            shotLEFT = false;
        }
    }
    if (ballPOSx >= 113 && ballPOSx <= 138) {
        if (oldY < 260 && ballPOSy >= 260) {
            oldY = 259;
            ballPOSy = 259;
            shotUP = true;
        }
        if (oldY > 291 && ballPOSy <= 291) {
            oldY = 292;
            ballPOSy = 292;
            shotUP = false;
        }
    }
    if (ballPOSx >= 168 && ballPOSx <= 233 && ballPOSy > 157 && ballPOSy <= 187) {
        slopeUP = true;
    }
    if (ballPOSx >= 168 && ballPOSx <= 233 && ballPOSy >= 231 && ballPOSy <= 261) {
        slopeDOWN = true;
    }
    if (ballPOSx >= 263 && ballPOSx <= 328 && ballPOSy >= 238 && ballPOSy <= 320) {
        slopeDOWN = true;
    }
    if (ballPOSx >= 120 && ballPOSx <= 163 && ballPOSy >= 163 && ballPOSy <= 238) {
        slopeRIGHT = true;
    }
    if (underGround) {
        slopeRIGHT = true;
    }
    if (ballPOSx < 160) {
        underGround = false;
    }
    if (ballPOSx > 240) {
        underGround = false;
    }
    }
    
    //LEVEL 11
    if (Level11) {
        fill(30, 168, 2);
        strokeWeight(5);
        stroke(173, 116, 2);
        rect(50, 90, 300, 220);
        fill(128, 86, 2);
        rect(50, 90, 55, 75);
        rect(50, 235, 55, 75);
        rect(295, 90, 55, 75);
        rect(295, 235, 55, 75);
        rect(165, 143, 70, 115);
        noStroke();
        fill(107, 72, 1);
        rect(48, 88, 55, 75);
        rect(48, 238, 55, 75);
        rect(298, 88, 55, 75);
        rect(298, 238, 55, 75);
        fill(0, 0, 0, 100);
        rect(55, 170, 40, 61);
        dX1 = 55;
        dX2 = 95;
        dY1 = 170;
        dY2 = 231;
        holePOSx = 322;
        holePOSy = 200;
        if (linePOS <= 0) {
            lineUP = false;
        }
        if (linePOS >= 30) {
            lineUP = true;
        }
        if (lineUP) {
            linePOS -= 1.5;
        } else {
            linePOS += 1.5;
        }
        fill(13, 184, 4);
        rect(108, 233, 55, 28);
        rect(238, 141, 55, 28);
        rect(238, 170, 55, 64);
        fill(3, 148, 8);
        rect(108, 141, 55, 28);
        rect(238, 233, 55, 28);
        strokeWeight(1);
        for (var bRep = 0; bRep < 3; bRep += 1) {
            stroke(0, 125, 0);
            line(110 + bRep * 20, 168, 115 + bRep * 20, 143);
            line(120 + bRep * 20, 168, 115 + bRep * 20, 143);
            line(240 + bRep * 20, 259, 245 + bRep * 20, 235);
            line(250 + bRep * 20, 259, 245 + bRep * 20, 235);
            stroke(90, 190, 90);
            line(110 + bRep * 20, 235, 115 + bRep * 20, 259);
            line(120 + bRep * 20, 235, 115 + bRep * 20, 259);
            line(240 + bRep * 20, 143, 245 + bRep * 20, 168);
            line(250 + bRep * 20, 143, 245 + bRep * 20, 168);
            line(240, 175 + bRep * 20, 288, 180 + bRep * 20);
            line(240, 185 + bRep * 20, 288, 180 + bRep * 20);
        }
        strokeWeight(5);
        stroke(100);
        line(104, 170 + (4 * linePOS)/3, 104, 190 + (4 * linePOS)/3);
        line(110 + linePOS, 165, 130 + linePOS, 165);
        line(160 - linePOS, 235, 140 - linePOS, 235);
        //Boundaries
    if (ballPOSy >= 305) {
        ballPOSy = 305;
        shotUP = true;
    }
    if (ballPOSx >= 345) {
        ballPOSx = 345;
        shotLEFT = true;
    }
    if (ballPOSy <= 96) {
        ballPOSy = 96;
        shotUP = false;
    }
    if (ballPOSx <= 56) {
        ballPOSx = 56;
        shotLEFT = false;
    }
    if (oldX > 111 && ballPOSx <= 111) {
        if (ballPOSy <= 165) {
            oldX = 112;
            ballPOSx = 112;
            shotLEFT = false;
        }
        if (ballPOSy >= 235) {
            oldX = 112;
            ballPOSx = 112;
            shotLEFT = false;
        }
    }
    if (oldX < 290 && ballPOSx >= 290) {
        if (ballPOSy <= 165) {
            oldX = 291;
            ballPOSx = 291;
            shotLEFT = true;
        }
        if (ballPOSy >= 235) {
            oldX = 291;
            ballPOSx = 291;
            shotLEFT = true;
        }
    }
    if (oldY > 171 && ballPOSy <= 171) {
        if (ballPOSx <= 105) {
            oldY = 172;
            ballPOSy = 172;
            shotUP = false;
        }
        if (ballPOSx >= 295) {
            oldY = 172;
            ballPOSy = 172;
            shotUP = false;
        }
    }
    if (oldY < 230 && ballPOSy >= 230) {
        if (ballPOSx <= 105) {
            oldY = 231;
            ballPOSy = 231;
            shotUP = true;
        }
        if (ballPOSx >= 295) {
            oldY = 231;
            ballPOSy = 231;
            shotUP = true;
        }
    }
    if (ballPOSx >= 165 && ballPOSx <= 235) {
        if (oldY < 138 && ballPOSy >= 138) {
            oldY = 137;
            ballPOSy = 137;
            shotUP = true;
        }
        if (oldY > 264 && ballPOSy <= 264) {
            oldY = 265;
            ballPOSy = 265;
            shotUP = false;
        }
    }
    if (ballPOSy >= 143 && ballPOSy <= 258) {
        if (oldX < 160 && ballPOSx >= 160) {
            oldX = 159;
            ballPOSx = 159;
            shotLEFT = true;
        }
        if (oldX > 241 && ballPOSx <= 241) {
            oldX = 242;
            ballPOSx = 242;
            shotLEFT = false;
        }
    }
    if (ballPOSy >= 170 + (4 * linePOS)/3 && ballPOSy <= 190 + (4 * linePOS)/3) {
        if (oldX < 99 && ballPOSx >= 99) {
            oldX = 98;
            ballPOSx = 98;
            shotLEFT = true;
        }
        if (oldX > 110 && ballPOSx <= 110) {
            oldX = 111;
            ballPOSx = 111;
            shotLEFT = false;
        }
    }
    if (ballPOSx >= 110 + linePOS && ballPOSx <= 130 + linePOS) {
        if (oldY < 160 && ballPOSy >= 160) {
            oldY = 159;
            ballPOSy = 159;
            shotUP = true;
        }
        if (oldY > 171 && ballPOSy <= 171) {
            oldY = 172;
            ballPOSy = 172;
            shotUP = false;
        }
    }
    if (ballPOSx >= 140 - linePOS && ballPOSx <= 160 - linePOS) {
        if (oldY < 230 && ballPOSy >= 230) {
            oldY = 229;
            ballPOSy = 229;
            shotUP = true;
        }
        if (oldY > 241 && ballPOSy <= 241) {
            oldY = 242;
            ballPOSy = 242;
            shotUP = false;
        }
    }
    if (ballPOSx >= 108 && ballPOSx <= 163 && ballPOSy >= 141 && ballPOSy <= 169) {
        slopeUP = true;
    }
    if (ballPOSx >= 238 && ballPOSx <= 293 && ballPOSy >= 233 && ballPOSy <= 261) {
        slopeUP = true;
    }
    if (ballPOSx >= 108 && ballPOSx <= 163 && ballPOSy >= 233 && ballPOSy <= 261) {
        slopeDOWN = true;
    }
    if (ballPOSx >= 238 && ballPOSx <= 293 && ballPOSy >= 141 && ballPOSy <= 169) {
        slopeDOWN = true;
    }
    if (ballPOSx >= 238 && ballPOSx <= 293 && ballPOSy >= 168 && ballPOSy <= 232) {
        slopeRIGHT = true;
    }
    }
    
    //LEVEL 12
    if (Level12) {
        fill(30, 168, 2);
        strokeWeight(5);
        stroke(173, 116, 2);
        rect(50, 100, 300, 200);
        noStroke();
        fill(0, 0, 0, 100);
        rect(75, 165, 40, 70);
        strokeWeight(2);
        fill(199, 190, 91);
        rect(140, 210, 40, 88);
        rect(220, 103, 40, 88);
        stroke(163, 163, 95);
        arc(160, 210, 40, 40, 180, 360);
        arc(240, 190, 40, 40, 0, 180);
        line(140, 210, 140, 296);
        line(180, 210, 180, 296);
        line(220, 105, 220, 190);
        line(260, 105, 260, 190);
        if (tips) {
        if (textDiminish > 0) {
            if (drop) {
                textDiminish -= 0.2;
            } else {
                textDiminish -= 5;
            }
        }
        textSize(11);
        fill(255, 255, 0, textDiminish);
        text("This hole contains bunkers. Try to avoid them.", 90, 90);
        }
        holePOSx = 300;
        holePOSy = 200;
        dX1 = 75;
        dX2 = 115;
        dY1 = 165;
        dY2 = 235;
        //Boundaries
    if (ballPOSy >= 295) {
        ballPOSy = 295;
        shotUP = true;
    }
    if (ballPOSx >= 345) {
        ballPOSx = 345;
        shotLEFT = true;
    }
    if (ballPOSy <= 106) {
        ballPOSy = 106;
        shotUP = false;
    }
    if (ballPOSx <= 56) {
        ballPOSx = 56;
        shotLEFT = false;
    }
    if (ballPOSx >= 140 && ballPOSx <= 180 && ballPOSy >= 210) {
        bunker = true;
    }
    if (dist(ballPOSx, ballPOSy, 160, 210) < 20) {
        bunker = true;
    }
    if (ballPOSx >= 220 && ballPOSx <= 260 && ballPOSy <= 190) {
        bunker = true;
    }
    if (dist(ballPOSx, ballPOSy, 240, 190) < 20) {
        bunker = true;
    }
    }
    
    //LEVEL 13
    if (Level13) {
        fill(30, 168, 2);
        strokeWeight(5);
        stroke(173, 116, 2);
        rect(50, 110, 300, 180);
        noStroke();
        fill(0, 0, 0, 100);
        rect(55, 215, 52, 71);
        fill(13, 184, 4);
        rect(53, 113, 295, 75);
        stroke(173, 116, 2);
        fill(92, 62, 1);
        rect(195, 110, 10, 75);
        noStroke();
        strokeWeight(2);
        fill(199, 190, 91);
        rect(110, 230, 190, 58);
        rect(130, 210, 150, 78);
        stroke(163, 163, 95);
        arc(130, 230, 40, 40, 180, 270);
        arc(280, 230, 40, 40, 270, 360);
        line(110, 230, 110, 286);
        line(300, 230, 300, 286);
        line(130, 210, 280, 210);
        strokeWeight(1);
        for (var bRep = 0; bRep < 7; bRep += 1) {
            stroke(90, 190, 90);
            line(60 + bRep * 20, 118, 65 + bRep * 20, 182);
            line(70 + bRep * 20, 118, 65 + bRep * 20, 182);
            line(210 + bRep * 20, 118, 215 + bRep * 20, 182);
            line(220 + bRep * 20, 118, 215 + bRep * 20, 182);
        }
        dX1 = 55;
        dX2 = 107;
        dY1 = 215;
        dY2 = 286;
        holePOSx = 325;
        holePOSy = 260;
        //Boundaries
    if (ballPOSy >= 285) {
        ballPOSy = 285;
        shotUP = true;
    }
    if (ballPOSx >= 345) {
        ballPOSx = 345;
        shotLEFT = true;
    }
    if (ballPOSy <= 116) {
        ballPOSy = 116;
        shotUP = false;
    }
    if (ballPOSx <= 56) {
        ballPOSx = 56;
        shotLEFT = false;
    }
    if (ballPOSy <= 188) {
        if (oldX < 190 && ballPOSx >= 190) {
            oldX = 189;
            ballPOSx = 189;
            shotLEFT = true;
        }
        if (oldX > 211 && ballPOSx <= 211) {
            oldX = 212;
            ballPOSx = 212;
            shotLEFT = false;
        }
    }
    if (ballPOSx >= 190 && ballPOSx <= 211 && oldY > 191 && ballPOSy <= 191) {
        oldY = 192;
        ballPOSy = 192;
        shotUP = false;
    }
    if (ballPOSy <= 188) {
        slopeDOWN = true;
    }
    if (ballPOSx >= 110 && ballPOSx <= 300 && ballPOSy >= 230) {
        bunker = true;
    }
    if (ballPOSx >= 130 && ballPOSx <= 280 && ballPOSy >= 210) {
        bunker = true;
    }
    if (dist(ballPOSx, ballPOSy, 130, 230) < 20) {
        bunker = true;
    }
    if (dist(ballPOSx, ballPOSy, 280, 230) < 20) {
        bunker = true;
    }
    }
    
    //LEVEL 14
    if (Level14) {
        fill(30, 168, 2);
        strokeWeight(5);
        stroke(173, 116, 2);
        rect(50, 100, 300, 200);
        noStroke();
        fill(0, 0, 0, 100);
        rect(75, 165, 40, 70);
        strokeWeight(2);
        fill(199, 190, 91);
        rect(170, 285, 178, 13);
        rect(190, 265, 138, 33);
        rect(325, 103, 23, 195);
        rect(170, 103, 178, 13);
        rect(190, 103, 138, 33);
        rect(305, 245, 20, 20);
        rect(305, 136, 20, 20);
        stroke(163, 163, 95);
        arc(190, 285, 40, 40, 180, 270);
        arc(190, 116, 40, 40, 90, 180);
        fill(30, 168, 2);
        arc(305, 156, 40, 40, 270, 360);
        arc(305, 245, 40, 40, 0, 90);
        line(170, 285, 170, 296);
        line(170, 104, 170, 116);
        line(190, 265, 302, 265);
        line(190, 136, 302, 136);
        line(325, 156, 325, 245);
        fill(0, 115, 220);
        noStroke();
        rect(170, 180, 125, 40);
        rect(190, 160, 85, 80);
        stroke(80, 150, 205);
        arc(190, 180, 40, 40, 180, 270);
        arc(275, 180, 40, 40, 270, 360);
        arc(275, 220, 40, 40, 0, 90);
        arc(190, 220, 40, 40, 90, 180);
        line(170, 180, 170, 220);
        line(190, 160, 275, 160);
        line(295, 180, 295, 220);
        line(190, 240, 275, 240);
        if (tips) {
        if (textDiminish > 0) {
            if (drop) {
                textDiminish -= 0.2;
            } else {
                textDiminish -= 5;
            }
        }
        textSize(11);
        fill(255, 255, 0, textDiminish);
        text("Don't putt your ball into the water", 120, 90);
        }
        holePOSx = 310;
        holePOSy = 200;
        dX1 = 75;
        dX2 = 115;
        dY1 = 165;
        dY2 = 235;
        //Boundaries
    if (ballPOSy >= 295) {
        ballPOSy = 295;
        shotUP = true;
    }
    if (ballPOSx >= 345) {
        ballPOSx = 345;
        shotLEFT = true;
    }
    if (ballPOSy <= 106) {
        ballPOSy = 106;
        shotUP = false;
    }
    if (ballPOSx <= 56) {
        ballPOSx = 56;
        shotLEFT = false;
    }
    if (ballPOSx >= 170 && ballPOSy <= 116) {
        bunker = true;
    }
    if (ballPOSx >= 190 && ballPOSy <= 136) {
        bunker = true;
    }
    if (ballPOSx >= 170 && ballPOSy >= 285) {
        bunker = true;
    }
    if (ballPOSx >= 190 && ballPOSy >= 265) {
        bunker = true;
    }
    if (ballPOSx >= 325) {
        bunker = true;
    }
    if (dist(ballPOSx, ballPOSy, 190, 116) < 20) {
        bunker = true;
    }
    if (dist(ballPOSx, ballPOSy, 190, 285) < 20) {
        bunker = true;
    }
    if (ballPOSx >= 305 && ballPOSy <= 156 && dist(ballPOSx, ballPOSy, 305, 156) > 20) {
        bunker = true;
    }
    if (ballPOSx >= 305 && ballPOSy >= 265 && dist(ballPOSx, ballPOSy, 305, 265) > 20) {
        bunker = true;
    }
    if (ballPOSx >= 170 && ballPOSx <= 295 && ballPOSy >= 180 && ballPOSy <= 220) {
        water = true;
    }
    if (ballPOSx >= 190 && ballPOSx <= 275 && ballPOSy >= 160 && ballPOSy <= 240) {
        water = true;
    }
    if (dist(ballPOSx, ballPOSy, 190, 180) < 20) {
        water = true;
    }
    if (dist(ballPOSx, ballPOSy, 275, 180) < 20) {
        water = true;
    }
    if (dist(ballPOSx, ballPOSy, 275, 220) < 20) {
        water = true;
    }
    if (dist(ballPOSx, ballPOSy, 190, 220) < 20) {
        water = true;
    }
    }
    
    //LEVEL 15
    if (Level15) {
        fill(30, 168, 2);
        strokeWeight(5);
        stroke(173, 116, 2);
        rect(50, 50, 300, 300);
        line(50, 100, 300, 100);
        line(300, 100, 300, 300);
        line(100, 300, 300, 300);
        line(100, 150, 100, 300);
        line(100, 150, 250, 150);
        line(250, 150, 250, 250);
        line(150, 250, 250, 250);
        line(150, 200, 150, 250);
        line(150, 200, 200, 200);
        noStroke();
        fill(0, 0, 0, 100);
        rect(55, 55, 40, 40);
        fill(13, 184, 4);
        rect(97, 53, 205, 45);
        rect(53, 103, 199, 45);
        rect(103, 153, 100, 45);
        rect(303, 53, 45, 250);
        rect(253, 103, 45, 150);
        rect(204, 153, 44, 50);
        fill(3, 148, 8);
        rect(53, 148, 45, 200);
        rect(103, 198, 45, 100);
        rect(203, 203, 45, 45);
        rect(99, 303, 249, 45);
        rect(149, 253, 149, 45);
        dX1 = 55;
        dX2 = 95;
        dY1 = 55;
        dY2 = 95;
        holePOSx = 178;
        holePOSy = 225;
        strokeWeight(1);
        for (var bRep = 0; bRep < 45; bRep += 15) {
            stroke(0, 125, 0);
            line(55 + bRep, 345, 60 + bRep, 150);
            line(65 + bRep, 345, 60 + bRep, 150);
            line(345, 305 + bRep, 100, 310 + bRep);
            line(345, 315 + bRep, 100, 310 + bRep);
            line(105 + bRep, 295, 110 + bRep, 200);
            line(115 + bRep, 295, 110 + bRep, 200);
            line(295, 255 + bRep, 150, 260 + bRep);
            line(295, 265 + bRep, 150, 260 + bRep);
            line(245, 205 + bRep, 205, 210 + bRep);
            line(245, 215 + bRep, 205, 210 + bRep);
            stroke(90, 190, 90);
            line(100, 55 + bRep, 300, 60 + bRep);
            line(100, 65 + bRep, 300, 60 + bRep);
            line(305 + bRep, 55, 310 + bRep, 300);
            line(315 + bRep, 55, 310 + bRep, 300);
            line(55, 105 + bRep, 250, 110 + bRep);
            line(55, 115 + bRep, 250, 110 + bRep);
            line(255 + bRep, 105, 260 + bRep, 250);
            line(265 + bRep, 105, 260 + bRep, 250);
            line(105, 155 + bRep, 200, 160 + bRep);
            line(105, 165 + bRep, 200, 160 + bRep);
            line(205 + bRep, 155, 210 + bRep, 200);
            line(215 + bRep, 155, 210 + bRep, 200);
        }
        //Boundaries
    if (ballPOSy >= 345) {
        ballPOSy = 345;
        shotUP = true;
    }
    if (ballPOSx >= 345) {
        ballPOSx = 345;
        shotLEFT = true;
    }
    if (ballPOSy <= 56) {
        ballPOSy = 56;
        shotUP = false;
    }
    if (ballPOSx <= 56) {
        ballPOSx = 56;
        shotLEFT = false;
    }
    if (ballPOSx <= 300) {
        if (oldY < 95 && ballPOSy >= 95) {
            oldY = 94;
            ballPOSy = 94;
            shotUP = true;
        }
        if (oldY > 106 && ballPOSy <= 106) {
            oldY = 107;
            ballPOSy = 107;
            shotUP = false;
        }
    }
    if (ballPOSy >= 100 && ballPOSy <= 300) {
        if (oldX < 295 && ballPOSx >= 295) {
            oldX = 294;
            ballPOSx = 294;
            shotLEFT = true;
        }
        if (oldX > 306 && ballPOSx <= 306) {
            oldX = 307;
            ballPOSx = 307;
            shotLEFT = false;
        }
    }
    if (ballPOSx >= 100 && ballPOSx <= 300) {
        if (oldY < 295 && ballPOSy >= 295) {
            oldY = 294;
            ballPOSy = 294;
            shotUP = true;
        }
        if (oldY > 306 && ballPOSy <= 306) {
            oldY = 307;
            ballPOSy = 307;
            shotUP = false;
        }
    }
    if (ballPOSy >= 150 && ballPOSy <= 300) {
        if (oldX < 95 && ballPOSx >= 95) {
            oldX = 94;
            ballPOSx = 94;
            shotLEFT = true;
        }
        if (oldX > 106 && ballPOSx <= 106) {
            oldX = 107;
            ballPOSx = 107;
            shotLEFT = false;
        }
    }
    if (ballPOSx >= 100 && ballPOSx <= 250) {
        if (oldY < 145 && ballPOSy >= 145) {
            oldY = 144;
            ballPOSy = 144;
            shotUP = true;
        }
        if (oldY > 156 && ballPOSy <= 156) {
            oldY = 157;
            ballPOSy = 157;
            shotUP = false;
        }
    }
    if (ballPOSy >= 150 && ballPOSy <= 250) {
        if (oldX < 245 && ballPOSx >= 245) {
            oldX = 244;
            ballPOSx = 244;
            shotLEFT = true;
        }
        if (oldX > 256 && ballPOSx <= 256) {
            oldX = 257;
            ballPOSx = 257;
            shotLEFT = false;
        }
    }
    if (ballPOSx >= 150 && ballPOSx <= 250) {
        if (oldY < 245 && ballPOSy >= 245) {
            oldY = 244;
            ballPOSy = 244;
            shotUP = true;
        }
        if (oldY > 256 && ballPOSy <= 256) {
            oldY = 257;
            ballPOSy = 257;
            shotUP = false;
        }
    }
    if (ballPOSy >= 200 && ballPOSy <= 250) {
        if (oldX < 145 && ballPOSx >= 145) {
            oldX = 144;
            ballPOSx = 144;
            shotLEFT = true;
        }
        if (oldX > 156 && ballPOSx <= 156) {
            oldX = 157;
            ballPOSx = 157;
            shotLEFT = false;
        }
    }
    if (ballPOSx >= 150 && ballPOSx <= 200) {
        if (oldY < 195 && ballPOSy >= 195) {
            oldY = 194;
            ballPOSy = 194;
            shotUP = true;
        }
        if (oldY > 206 && ballPOSy <= 206) {
            oldY = 207;
            ballPOSy = 207;
            shotUP = false;
        }
    }
    if (ballPOSx >= 97 && ballPOSx <= 302 && ballPOSy >= 53 && ballPOSy <= 98) {
        slopeRIGHT = true;
    }
    if (ballPOSx >= 303 && ballPOSx <= 348 && ballPOSy >= 53 && ballPOSy <= 303) {
        slopeDOWN = true;
    }
    if (ballPOSx >= 53 && ballPOSx <= 252 && ballPOSy >= 103 && ballPOSy <= 148) {
        slopeRIGHT = true;
    }
    if (ballPOSx >= 253 && ballPOSx <= 298 && ballPOSy >= 103 && ballPOSy <= 253) {
        slopeDOWN = true;
    }
    if (ballPOSx >= 103 && ballPOSx <= 203 && ballPOSy >= 153 && ballPOSy <= 198) {
        slopeRIGHT = true;
    }
    if (ballPOSx >= 204 && ballPOSx <= 248 && ballPOSy >= 153 && ballPOSy <= 203) {
        slopeDOWN = true;
    }
    if (ballPOSx >= 53 && ballPOSx <= 98 && ballPOSy >= 148 && ballPOSy <= 348) {
        slopeUP = true;
    }
    if (ballPOSx >= 99 && ballPOSx <= 348 && ballPOSy >= 303 && ballPOSy <= 348) {
        slopeLEFT = true;
    }
    if (ballPOSx >= 103 && ballPOSx <= 148 && ballPOSy >= 198 && ballPOSy <= 298) {
        slopeUP = true;
    }
    if (ballPOSx >= 149 && ballPOSx <= 298 && ballPOSy >= 253 && ballPOSy <= 298) {
        slopeLEFT = true;
    }
    if (ballPOSx >= 203 && ballPOSx <= 248 && ballPOSy >= 203 && ballPOSy <= 248) {
        slopeLEFT = true;
    }
    }
    
    //LEVEL 16
    if (Level16) {
        fill(30, 168, 2);
        strokeWeight(5);
        stroke(173, 116, 2);
        rect(50, 100, 300, 200);
        noStroke();
        fill(13, 184, 4);
        rect(162, 103, 15, 195);
        rect(202, 103, 15, 195);
        rect(242, 103, 15, 195);
        fill(3, 148, 8);
        rect(142, 103, 15, 195);
        rect(182, 103, 15, 195);
        rect(222, 103, 15, 195);
        rect(53, 153, 45, 70);
        rect(304, 147, 44, 130);
        fill(0, 0, 0, 100);
        rect(55, 225, 38, 71);
        fill(0, 115, 220);
        rect(98, 103, 30, 195);
        rect(272, 103, 30, 195);
        stroke(80, 150, 205);
        strokeWeight(2);
        line(98, 104, 98, 296);
        line(128, 104, 128, 296);
        line(272, 104, 272, 296);
        line(302, 104, 302, 296);
        stroke(100);
        strokeWeight(5);
        line(93, 105 + linePOS, 133, 105 + linePOS); 
        line(93, 125 + linePOS, 133, 125 + linePOS);
        line(267, 295 - linePOS, 307, 295 - linePOS);
        line(267, 275 - linePOS, 307, 275 - linePOS);
        noStroke();
        fill(125);
        rect(98, 108 + linePOS, 30, 15);
        rect(272, 278 - linePOS, 30, 15);
        strokeWeight(5);
        stroke(173, 116, 2);
        line(97, 180, 97, 298);
        line(303, 102, 303, 220);
        strokeWeight(1);
        for (var bRep = 0; bRep < 42; bRep += 14) {
            stroke(0, 125, 0);
            line(55 + bRep, 220, 60 + bRep, 155);
            line(65 + bRep, 220, 60 + bRep, 155);
            line(307 + bRep, 270, 312 + bRep, 150);
            line(317 + bRep, 270, 312 + bRep, 150);
        }
        for (var bRep = 0; bRep < 200; bRep += 20) {
            stroke(0, 125, 0);
            line(154, 105 + bRep, 145, 110 + bRep);
            line(154, 115 + bRep, 145, 110 + bRep);
            line(194, 105 + bRep, 185, 110 + bRep);
            line(194, 115 + bRep, 185, 110 + bRep);
            line(234, 105 + bRep, 225, 110 + bRep);
            line(234, 115 + bRep, 225, 110 + bRep);
            stroke(90, 190, 90);
            line(165, 105 + bRep, 174, 110 + bRep);
            line(165, 115 + bRep, 174, 110 + bRep);
            line(205, 105 + bRep, 214, 110 + bRep);
            line(205, 115 + bRep, 214, 110 + bRep);
            line(245, 105 + bRep, 254, 110 + bRep);
            line(245, 115 + bRep, 254, 110 + bRep);
        }
        if (linePOS <= 0) {
            lineUP = false;
        }
        if (linePOS >= 50) {
            lineUP = true;
        }
        if (lineUP) {
            linePOS -= 1;
        } else {
            linePOS += 1;
        }
        dX1 = 55;
        dX2 = 95;
        dY1 = 225;
        dY2 = 296;
        holePOSx = 325;
        holePOSy = 125;
        //Boundaries
    if (ballPOSy >= 295) {
        ballPOSy = 295;
        shotUP = true;
    }
    if (ballPOSx >= 345) {
        ballPOSx = 345;
        shotLEFT = true;
    }
    if (ballPOSy <= 106) {
        ballPOSy = 106;
        shotUP = false;
    }
    if (ballPOSx <= 56) {
        ballPOSx = 56;
        shotLEFT = false;
    }
    if (ballPOSy >= 180) {
        if (oldX < 92 && ballPOSx >= 92) {
            oldX = 91;
            ballPOSx = 91;
            shotLEFT = true;
        }
        if (oldX > 103 && ballPOSx <= 103) {
            oldX = 104;
            ballPOSx = 104;
            shotLEFT = false;
        }
    }
    if (ballPOSy <= 220) {
        if (oldX < 298 && ballPOSx >= 298) {
            oldX = 297;
            ballPOSx = 297;
            shotLEFT = true;
        }
        if (oldX > 309 && ballPOSx <= 309) {
            oldX = 310;
            ballPOSx = 310;
            shotLEFT = false;
        }
    }
    if (ballPOSx >= 90 && ballPOSx <= 136) {
        if (oldY < 100 + linePOS && ballPOSy >= 100 + linePOS) {
            oldY = 99 + linePOS;
            ballPOSy = 99 + linePOS;
            shotUP = true;
        }
        if (oldY > 111 + linePOS && ballPOSy <= 111 + linePOS) {
            oldY = 112 + linePOS;
            ballPOSy = 112 + linePOS;
            shotUP = false;
        }
        if (oldY < 120 + linePOS && ballPOSy >= 120 + linePOS) {
            oldY = 119 + linePOS;
            ballPOSy = 119 + linePOS;
            shotUP = true;
        }
        if (oldY > 131 + linePOS && ballPOSy <= 131 + linePOS) {
            oldY = 132 + linePOS;
            ballPOSy = 132 + linePOS;
            shotUP = false;
        }
    }
    if (ballPOSx >= 98 && ballPOSx <= 128) {
        if (ballPOSy <= 100 + linePOS) {
            water = true;
        }
        if (ballPOSy >= 131 + linePOS) {
            water = true;
        }
        if (ballPOSy > 100 + linePOS && ballPOSy < 131 + linePOS) {
            if (lineUP) {
                ballPOSy -= 1;
            } else {
                ballPOSy += 1;
            }
        }
    }
    if (ballPOSx >= 264 && ballPOSx <= 310) {
        if (oldY < 270 - linePOS && ballPOSy >= 270 - linePOS) {
            oldY = 269 - linePOS;
            ballPOSy = 269 - linePOS;
            shotUP = true;
        }
        if (oldY > 281 - linePOS && ballPOSy <= 281 - linePOS) {
            oldY = 282 - linePOS;
            ballPOSy = 282 - linePOS;
            shotUP = false;
        }
        if (oldY < 290 - linePOS && ballPOSy >= 290 - linePOS) {
            oldY = 289 - linePOS;
            ballPOSy = 289 - linePOS;
            shotUP = true;
        }
        if (oldY > 301 - linePOS && ballPOSy <= 301 - linePOS) {
            oldY = 302 - linePOS;
            ballPOSy = 302 - linePOS;
            shotUP = false;
        }
    }
    if (ballPOSx >= 272 && ballPOSx <= 302) {
        if (ballPOSy <= 270 - linePOS) {
            water = true;
        }
        if (ballPOSy >= 301 - linePOS) {
            water = true;
        }
        if (ballPOSy > 270 - linePOS && ballPOSy < 301 - linePOS) {
            if (lineUP) {
                ballPOSy -= 1;
            } else {
                ballPOSy += 1;
            }
        }
    }
    if (ballPOSx >= 53 && ballPOSx <= 98 && ballPOSy >= 153 && ballPOSy <= 223) {
        slopeUP = true;
    }
    if (ballPOSx >= 304 && ballPOSx <= 348 && ballPOSy >= 147 && ballPOSy <= 277) {
        slopeUP = true;
    }
    if (ballPOSx >= 142 && ballPOSx <= 157 && ballPOSy >= 103 && ballPOSy <= 298) {
        slopeLEFT = true;
    }
    if (ballPOSx >= 182 && ballPOSx <= 197 && ballPOSy >= 103 && ballPOSy <= 298) {
        slopeLEFT = true;
    }
    if (ballPOSx >= 222 && ballPOSx <= 237 && ballPOSy >= 103 && ballPOSy <= 298) {
        slopeLEFT = true;
    }
    if (ballPOSx >= 162 && ballPOSx <= 177 && ballPOSy >= 103 && ballPOSy <= 298) {
        slopeRIGHT = true;
    }
    if (ballPOSx >= 202 && ballPOSx <= 217 && ballPOSy >= 103 && ballPOSy <= 298) {
        slopeRIGHT = true;
    }
    }
    
    //LEVEL 17
    if (Level17) {
        fill(30, 168, 2);
        strokeWeight(5);
        stroke(173, 116, 2);
        rect(50, 65, 230, 100);
        rect(50, 230, 250, 120);
        line(150, 280, 220, 280);
        line(150, 300, 220, 300);
        fill(128, 86, 2);
        rect(200, 230, 25, 50);
        rect(200, 300, 25, 50);
        rect(225, 230, 75, 25);
        rect(225, 325, 75, 25);
        noStroke();
        rect(205, 233, 50, 20);
        rect(205, 328, 50, 20);
        fill(0, 0, 0, 100);
        rect(55, 255, 40, 70);
        strokeWeight(2);
        fill(175);
        stroke(125);
        beginShape();
        vertex(303, 310);
        vertex(303, 325);
        vertex(335, 325);
        vertex(335, 107);
        vertex(283, 107);
        vertex(283, 122);
        vertex(320, 122);
        vertex(320, 310);
        vertex(303, 310);
        endShape();
        beginShape();
        vertex(303, 282);
        vertex(303, 297);
        vertex(360, 297);
        vertex(360, 85);
        vertex(283, 85);
        vertex(283, 100);
        vertex(345, 100);
        vertex(345, 282);
        vertex(303, 282);
        endShape();
        beginShape();
        vertex(277, 228);
        vertex(292, 228);
        vertex(292, 205);
        vertex(307, 185);
        vertex(307, 142);
        vertex(283, 130);
        vertex(283, 150);
        vertex(292, 155);
        vertex(292, 180);
        vertex(277, 200);
        vertex(277, 228);
        endShape();
        noStroke();
        strokeWeight(1);
        fill(3, 148, 8);
        rect(148, 283, 80, 15);
        rect(140, 68, 60, 95);
        stroke(0, 125, 0);
        line(228, 285, 150, 290);
        line(228, 295, 150, 290);
        for (var bRep = 0; bRep < 100; bRep += 20) {
            line(198, 70 + bRep, 143, 75 + bRep);
            line(198, 80 + bRep, 143, 75 + bRep);
        }
        for (var cRep = 0; cRep < 3; cRep += 1) {
            stroke(0, 0, 0, 90 - cRep * 30);
            line(277 - cRep, 85, 277 - cRep, 100);
            line(277 - cRep, 107, 277 - cRep, 122);
            line(277 - cRep, 130, 277 - cRep, 145);
        }
        noStroke();
        if (tips) {
        if (textDiminish > 0) {
            if (drop) {
                textDiminish -= 0.2;
            } else {
                textDiminish -= 5;
            }
        }
        textSize(11);
        fill(255, 255, 0, textDiminish);
        text("Go into one of the holes to send the ball out the other side", 60, 60);
        }
        dX1 = 55;
        dX2 = 95;
        dY1 = 255;
        dY2 = 325;
        holePOSx = 100;
        holePOSy = 115;
        //Boundaries
    if (ballPOSy >= 345) {
        ballPOSy = 345;
        shotUP = true;
    }
    if (ballPOSx >= 295) {
        ballPOSx = 295;
        shotLEFT = true;
    }
    if (ballPOSy <= 71) {
        ballPOSy = 71;
        shotUP = false;
    }
    if (ballPOSx <= 56) {
        ballPOSx = 56;
        shotLEFT = false;
    }
    if (oldY < 160 && ballPOSy >= 160) {
        oldY = 159;
        ballPOSy = 159;
        shotUP = true;
    }
    if (oldY > 236 && ballPOSy <= 236) {
        oldY = 237;
        ballPOSy = 237;
        shotUP = false;
    }
    if (ballPOSy < 200 && ballPOSx >= 275) {
        ballPOSx = 275;
        shotLEFT = true;
    }
    if (ballPOSx >= 150 && ballPOSx <= 220) {
        if (oldY < 275 && ballPOSy >= 275) {
            oldY = 274;
            ballPOSy = 274;
            shotUP = true;
        }
        if (oldY > 286 && ballPOSy <= 286) {
            oldY = 287;
            ballPOSy = 287;
            shotUP = false;
        }
        if (oldY < 295 && ballPOSy >= 295) {
            oldY = 294;
            ballPOSy = 294;
            shotUP = true;
        }
        if (oldY > 306 && ballPOSy <= 306) {
            oldY = 307;
            ballPOSy = 307;
            shotUP = false;
        }
    }
    if (oldX < 195 && ballPOSx >= 195) {
        if (ballPOSy >= 300) {
            oldX = 194;
            ballPOSx = 194;
            shotLEFT = true;
        }
        if (ballPOSy <= 280 && ballPOSy >= 200) {
            oldX = 194;
            ballPOSx = 194;
            shotLEFT = true;
        }
    }
    if (oldX > 231 && ballPOSx <= 231) {
        if (ballPOSy >= 300) {
            oldX = 232;
            ballPOSx = 232;
            shotLEFT = false;
        }
        if (ballPOSy <= 280 && ballPOSy >= 200) {
            oldX = 232;
            ballPOSx = 232;
            shotLEFT = false;
        }
    }
    if (ballPOSx >= 210) {
        if (oldY > 261 && ballPOSy <= 261) {
            oldY = 262;
            ballPOSy = 262;
            shotUP = false;
        }
        if (oldY < 320 && ballPOSy >= 320) {
            oldY = 319;
            ballPOSy = 319;
            shotUP = true;
        }
    }
    if (ballPOSx >= 148 && ballPOSx <= 228 && ballPOSy >= 283 && ballPOSy <= 298) {
        slopeLEFT = true;
    }
    if (ballPOSx >= 140 && ballPOSx <= 200 && ballPOSy <= 200) {
        slopeLEFT = true;
    }
    fill(0, 0, 0, 100);
    ellipse(285, 270, 14, 14);
    ellipse(285, 270, 10, 10);
    if (dist(ballPOSx, ballPOSy, 285, 270) <= 10 - (speedX + speedY)/3 && speedX < 8 && speedY < 8) {
        ballPOSx = 285;
        ballPOSy = 270;
        speedX = 0;
        speedY = 0;
        resetShot = false;
        if (delayTimer < 40) {
            if (delayTimer >= 10) {
            underGround = true;
            }
            delayTimer += 1;
        } else {
            underGround = false;
            delayTimer = 0;
            ballPOSx = 280;
            ballPOSy = 137;
            shotLEFT = true;
            shotUP = true;
            speedX = 14;
            speedY = 7;
            shotDiminish = 11;
        }
    }
    fill(0, 0, 0, 100);
    ellipse(285, 290, 14, 14);
    ellipse(285, 290, 10, 10);
    if (dist(ballPOSx, ballPOSy, 285, 290) <= 10 - (speedX + speedY)/3 && speedX < 8 && speedY < 8) {
        ballPOSx = 285;
        ballPOSy = 290;
        speedX = 0;
        speedY = 0;
        resetShot = false;
        if (delayTimer < 40) {
            if (delayTimer >= 10) {
            underGround = true;
            }
            delayTimer += 1;
        } else {
            underGround = false;
            delayTimer = 0;
            ballPOSx = 280;
            ballPOSy = 92;
            shotLEFT = true;
            speedX = 20;
            shotDiminish = 10;
        }
    }
    fill(0, 0, 0, 100);
    ellipse(285, 310, 14, 14);
    ellipse(285, 310, 10, 10);
    if (dist(ballPOSx, ballPOSy, 285, 308) <= 10 - (speedX + speedY)/3 && speedX < 8 && speedY < 8) {
        ballPOSx = 285;
        ballPOSy = 310;
        speedX = 0;
        speedY = 0;
        resetShot = false;
        if (delayTimer < 40) {
            if (delayTimer >= 10) {
            underGround = true;
            }
            delayTimer += 1;
        } else {
            underGround = false;
            delayTimer = 0;
            ballPOSx = 280;
            ballPOSy = 115;
            shotLEFT = true;
            speedX = 20;
            shotDiminish = 10;
        }
    }
    }
    
    //LEVEL 18
    if (Level18) {
        fill(30, 168, 2);
        strokeWeight(5);
        stroke(173, 116, 2);
        rect(50, 75, 300, 250);
        rect(284, 325, 66, 100);
        line(284, 260, 315, 260);
        line(315, 120, 315, 260);
        fill(133, 89, 2);
        rect(99, 75, 185, 185);
        noStroke();
        fill(30, 168, 2);
        rect(287, 320, 61, 10);
        fill(125);
        rect(97, 78, 100, 50);
        rect(192, 208, 95, 50);
        var cX = 192;
        var cY = 168;
        var cD = 180;
        fill(13, 184, 4);
        rect(287, 78, 30, 40);
        rect(318, 78, 30, 184);
        rect(287, 263, 60, 140);
        rect(53, 263, 44, 60);
        fill(3, 148, 8);
        rect(287, 118, 26, 140);
        strokeWeight(1);
        for (var bRep = 0; bRep < 30; bRep += 15) {
            stroke(0, 125, 0);
            line(288 + bRep, 255, 293 + bRep, 121);
            line(298 + bRep, 255, 293 + bRep, 121);
            stroke(90, 190, 90);
            line(320 + bRep, 80, 325 + bRep, 260);
            line(330 + bRep, 80, 325 + bRep, 260);
        }
        for (var aRep = 0; aRep < 36; aRep += 12) {
            line(288, 80 + aRep, 314, 85 + aRep);
            line(288, 90 + aRep, 314, 85 + aRep);
        }
        strokeWeight(4);
        for (var cRep = 0; cRep < 16; cRep += 1) {
            if (selection === cRep && underGround) {
                fill(230, 230, 28);
            } else {
                fill(150);
            }
            stroke(125);
            arc(cX, cY, cD, cD, -90 + cRep * 22.5, -67.5 + cRep * 22.5);
        }
        for (var dRep = 0; dRep < 60; dRep += 20) {
            stroke(90, 190, 90);
            strokeWeight(1);
            line(292 + dRep, 265, 297 + dRep, 398);
            line(302 + dRep, 265, 297 + dRep, 398);
            line(55, 268 + dRep, 95, 273 + dRep);
            line(55, 278 + dRep, 95, 273 + dRep);
            stroke(105);
            strokeWeight(2);
            line(100 + dRep/2, 94, 110 + dRep/2, 100);
            line(100 + dRep/2, 106, 110 + dRep/2, 100);
            line(254 + dRep/2, 234, 264 + dRep/2, 240);
            line(254 + dRep/2, 246, 264 + dRep/2, 240);
        }
        stroke(125);
        strokeWeight(4);
        var FortuneString = ["+" + 1, -1, 0, "+"+ 2, -2, "Re", "+" + 3, -3, 0, "+" + 4, -4, 0, "+" + 5, -5, 0, "Spin"];
        textAlign(CENTER, CENTER);
        for (var bRep = 0; bRep < 16; bRep += 1) {
            line(cos(bRep * 22.5 - 90) * 90 + cX, sin(bRep * 22.5 - 90 ) * 90 + cY, cX, cY);
            fill(255);
            text(FortuneString[bRep], cos(bRep * 22.5 - 80) * 70 + cX, sin(bRep * 22.5 - 80) * 70 + cY);
        }
        textAlign(LEFT, BOTTOM);
        noStroke();
        fill(0, 0, 0, 100);
        rect(55, 80, 40, 70);
        strokeWeight(1);
        if (tips) {
        if (textDiminish > 0) {
            if (drop) {
                textDiminish -= 0.2;
            } else {
                textDiminish -= 5;
            }
        }
        textSize(11);
        fill(255, 255, 0, textDiminish);
        text("Putt your ball into the wheel or play it safe and go around", 63, 70);
        }
        dX1 = 55;
        dX2 = 95;
        dY1 = 80;
        dY2 = 150;
        holePOSx = 320;
        holePOSy = 500;
        if (ballPOSy > 400) {
            speedX = 0;
            speedY = 0;
            ballPOSx = holePOSx;
            ballPOSy = holePOSy;
        }
        //Boundaries
    if (ballPOSx <= 284 && oldY < 320 && ballPOSy >= 320) {
        oldY = 319;
        ballPOSy = 319;
        shotUP = true;
    }
    if (ballPOSx >= 345) {
        ballPOSx = 345;
        shotLEFT = true;
    }
    if (ballPOSy <= 81) {
        ballPOSy = 81;
        shotUP = false;
    }
    if (ballPOSx <= 56) {
        ballPOSx = 56;
        shotLEFT = false;
    }
    if (ballPOSy < 128 && oldX < 95 && ballPOSx >= 95) {
        underGround = true;
    }
    if (ballPOSy >= 320 && oldX > 290 && ballPOSx <= 290) {
        oldX = 291;
        ballPOSx = 291;
        shotLEFT = false;
    }
    if (ballPOSy >= 128 && ballPOSy <= 260 && oldX < 94 && ballPOSx >= 94) {
        oldX = 93;
        ballPOSx = 93;
        shotLEFT = true;
    }
    if (ballPOSx >= 99 && ballPOSx <= 315) {
        if (oldY > 266 && ballPOSy <= 266) {
            oldY = 267;
            ballPOSy = 267;
            shotUP = false;
        }
        if (oldY < 255 && ballPOSy >= 255) {
            oldY = 254;
            ballPOSy = 254;
            shotUP = true;
        }
    }
    if (ballPOSy >= 120 && ballPOSy <= 260) {
        if (oldX < 310 && ballPOSx >= 310) {
            oldX = 309;
            ballPOSx = 309;
            shotLEFT = true;
        }
        if (oldX > 321 && ballPOSx <= 321) {
            oldX = 322;
            ballPOSx = 322;
            shotLEFT = false;
        }
    }
    
    if (ballPOSx >= 284 && ballPOSx <= 317 && ballPOSy >= 118 && ballPOSy <= 260) {
        slopeUP = true;
    }
    if (ballPOSx >= 284 && ballPOSx <= 317 && ballPOSy <= 118) {
        slopeRIGHT = true;
    }
    if (ballPOSx >= 318 && ballPOSy <= 262) {
        slopeDOWN = true;
    }
    if (ballPOSx >= 284 && ballPOSy >= 260) {
        slopeDOWN = true;
    }

    if (ballPOSy <= 260 && oldX > 290 && ballPOSx <= 290) {
        oldX = 291;
        ballPOSx = 291;
        shotLEFT = false;
    }
    if (ballPOSx <= 97 && ballPOSy >= 263) {
        slopeRIGHT = true;
    }
    if (underGround) {
        delayTimer += speedX/2;
        ballPOSx = 290;
        ballPOSy = 233;
        if (PrevSpeedX > 0.1 && speedX <= 0.1) {
            delayTimer = 0;
        }
        if (speedX <= 0.1) {
            resetShot = false;
            if (selection === 0) {Bonus = 1;}
            if (selection === 1) {Bonus = -1;}
            if (selection === 3) {Bonus = 2;}
            if (selection === 4) {Bonus = -4;}
            if (selection === 5) {
                drop = true;
                speedX = 0;
                speedY = 0;
                delayTimer = 0;
                underGround = false;
            }
            if (selection === 6) {Bonus = 3;}
            if (selection === 7) {Bonus = -3;}
            if (selection === 9) {Bonus = 4;}
            if (selection === 10) {Bonus = -4;}
            if (selection === 12) {Bonus = 5;}
            if (selection === 13) {Bonus = -5;}
            if (selection === 15) {speedX = random(10, 30);}
            textAlign(CENTER, BOTTOM);
            textSize(20);
            delayTimer += 3;
            fill(255, 255, 255, 255 - delayTimer);
            text("Prize:  " + FortuneString[selection], 200, 70);
            textAlign(LEFT, BOTTOM);
            if (delayTimer >= 255) {
                shotUP = true;
                shotLEFT = false;
                speedX = 3;
                underGround = false;
            }
        } else {
            selection = round(delayTimer) % 16;
        }
    }
    }
    
    
    
    
    
    
    
    
        //Hole
    noStroke();
    fill(0, 0, 0, 100);
    ellipse(holePOSx, holePOSy, 14, 14);
    ellipse(holePOSx, holePOSy, 10, 10);
    if (dist(ballPOSx, ballPOSy, holePOSx, holePOSy) <= 10 - (speedX + speedY)/3 && speedX < 8 && speedY < 8 && !titleScreen && !endGame) {
        ballPOSx = holePOSx;
        ballPOSy = holePOSy;
        speedX = 0;
        speedY = 0;
        resetShot = false;
        fill(51, 39, 5);
        rect(eX + 10, eY, 180, 60);
        rect(eX, eY + 10, 200, 40);
        ellipse(eX + 10, eY + 10, 20, 20);
        ellipse(eX + 190, eY + 10, 20, 20);
        ellipse(eX + 10, eY + 50, 20, 20);
        ellipse(eX + 190, eY + 50, 20, 20);
        if (mouseX > eX + 20 && mouseX < eX + 180 && mouseY > eY && mouseY < eY + 60) {
            fill(150);
            if (mouseIsPressed && !endClick) {
                if (!LevelMenu) {
                if(Level18){endGame=true;Level18 = false;}
                if(Level17){Level18 = true;Level17 = false;}
                if(Level16){Level17 = true;Level16 = false;}
                if(Level15){Level16 = true;Level15 = false;}
                if(Level14){Level15 = true;Level14 = false;}
                if(Level13){Level14 = true;Level13 = false;}
                if(Level12){Level13 = true;Level12 = false;}
                if(Level11){Level12 = true;Level11 = false;}
                if(Level10){Level11 = true;Level10 = false;}
                if(Level9){Level10 = true;Level9 = false;}
                if(Level8){Level9 = true;Level8 = false;}
                if(Level7){Level8 = true;Level7 = false;}
                if(Level6){Level7 = true;Level6 = false;}
                if(Level5){Level6 = true;Level5 = false;}
                if(Level4){Level5 = true;Level4 = false;}
                if(Level3){Level4 = true;Level3 = false;}
                if(Level2){Level3 = true;Level2 = false;}
                if(Level1){Level2 = true;Level1 = false;}
                if (LevelSelect < 17) {
                    LevelSelect += 1;
                }
                drop = true;
                } else {
                    titleScreen = true;
                    Level1 = false;
                    Level2 = false;
                    Level3 = false;
                    Level4 = false;
                    Level5 = false;
                    Level6 = false;
                    Level7 = false;
                    Level8 = false;
                    Level9 = false;
                    Level10 = false;
                    Level11 = false;
                    Level12 = false;
                    Level13 = false;
                    Level14 = false;
                    Level15 = false;
                    Level16 = false;
                    Level17 = false;
                    Level18 = false;
                    drop = true;
                }
                endClick = true;
                textDiminish = 255;
            }
        } else {
            fill(60);
        }
        textSize(32);
        text("Next Hole", eX + 15, eY + 48);
        triangle(eX + 165, eY + 40, eX + 165, eY + 20, eX + 180, eY + 30);
        textSize(12);
        
    }
    
    //drop
    strokeWeight(1);
        if (LevelStart) {
            drop = true;
            shot = false;
            LevelStart = false;
        }
    if (drop) {
        ballPOSx = mouseX;
        ballPOSy = mouseY;
        if (ballPOSx <= dX1 + 3) {
            ballPOSx = dX1 + 3;
        }
        if (ballPOSx >= dX2 - 3) {
            ballPOSx = dX2 - 3;
        }
        if (ballPOSy <= dY1 + 3) {
            ballPOSy = dY1 + 3;
        }
        if (ballPOSy >= dY2 - 3) {
            ballPOSy = dY2 - 3;
        }
        fill(0);
        if (!titleScreen && !endGame && !endClick) {
            text("drop", mouseX - 12, mouseY - 20);
            if (mouseIsPressed && !endClick) {
                drop = false;
                endClick = true;
            }
        }
    } else {
        if (resetShot && !water && !titleScreen && !endGame) {
            stroke(0);
            fill(0);
            ellipse(mouseX - 5, mouseY, 10, 4);
            line(mouseX - 8, mouseY, mouseX - 11, mouseY - 20);
            if (mouseIsPressed && !endClick) {
                shot = true;
            }
            if (mouseX > ballPOSx) {
                shotLEFT = true;
                dotx = -powerX;
            } else {
                shotLEFT = false;
                dotx = powerX;
            }
            if (mouseY > ballPOSy) {
                shotUP = true;
                doty = -powerY;
            } else {
                shotUP = false;
                doty = powerY;
            }
            stroke(234, 234, 0);
            strokeWeight(5);
            for (var dotRep = 1; dotRep < 6; dotRep += 1) {
                point(ballPOSx + dotRep * dotx/4, ballPOSy + dotRep * doty/4);
            }
        }
    }
    
    //Ball
    strokeWeight(1);
    if (Level17) {
    stroke(200 - delayTimer * 20);
    fill(255 - delayTimer * 25.5);
    } else {
        stroke(200);
        fill(255);
    }
    if (!underGround && !underWater && !titleScreen && !endGame) {
    ellipse(ballPOSx, ballPOSy, 6, 6);
    }
    
    //Water
    if (water) {
        if (speedX < 15 && speedY < 15) {
            underWater = true;
        }
        if (speedX > 15) {
            speedX = 15;
        }
        if (speedY > 15) {
            speedY = 15;
        }
    }
    if (underWater) {
        waterTime += 1;
        speedX = 0;
        speedY = 0;
        noFill();
        for(var wRep = 0; wRep < 30; wRep += 10) {
            if (waterTime >= wRep) {
                stroke(80, 150, 205, 255 + wRep * 5 - waterTime * 10);
                ellipse(ballPOSx, ballPOSy, waterTime * 1.5 - wRep, waterTime * 1.5 - wRep);
            }
        }
        if (waterTime >= 60) {
            water = false;
            underWater = false;
            drop = true;
        }
    } else {
        waterTime = 0;
    }
    
    //Bunker
    if (bunker) {
        if (speedX > 0) {
            speedX = speedX/2;
        }
        if (speedY > 0) {
            speedY = speedY/2;
        }
    }
    
    //Score Display
    if (mouseX > 170 && mouseX < 230 && mouseY <= 10 && !titleScreen) {
        ScoreDisplay = true;
    }
    if (ScoreDisplay && dY < 80) {
        dY += 8;
    }
    if (mouseY > 80 && !endGame) {
        dY = 0;
        ScoreDisplay = false;
    }
    fill(185);
    noStroke();
    rect(0, dY - 80, 400, 80);
    fill(175);
    quad(0, dY - 80, 0, dY, 5, dY - 5, 5, dY - 75);
    quad(400, dY - 80, 400, dY, 395, dY - 5, 395, dY - 75);
    fill(200);
    quad(0, dY - 80, 5, dY - 75, 395, dY - 75, 400, dY - 80);
    quad(0, dY, 5, dY - 5, 395, dY - 5, 400, dY);
    fill(185);
    stroke(100);
    strokeWeight(1);
    if (!titleScreen) {
    quad(170, dY, 182, dY + 7, 218, dY + 7, 230, dY);
    line(0, dY - 1, 400, dY - 1);
    }
    stroke(0);
    strokeWeight(3);
    noFill();
        //Restart
        if (!titleScreen && !endGame) {
        arc(18, dY + 18, 22, 22, 120, 240);
        arc(18, dY + 18, 22, 22, -60, 60);
        noStroke();
        if (Level18 && !endGame) {
            fill(255, 0, 0);
            quad(5, 5, 10, 5, 32, 30, 27, 30);
            quad(5, 30, 10, 30, 32, 5, 27, 5);
        }
        fill(0);
        triangle(14, dY + 31, 14, dY + 24, 20, dY + 28);
        triangle(22, dY + 12, 22, dY + 5, 16, dY + 8);
        }
        textSize(10);
        if (dist(mouseX, mouseY, 18, dY + 18) <= 11 && !titleScreen && !Level18) {
            fill(0);
            if (!drop) {
            text("Restart Hole", 5, dY + 42);
            }
            if (mouseIsPressed && !endClick) {
                drop = true;
                speedX = 0;
                if(Level1){L1S = 0;}
                if(Level2){L2S = 0;}
                if(Level3){L3S = 0;}
                if(Level4){L4S = 0;}
                if(Level5){L5S = 0;}
                if(Level6){L6S = 0;}
                if(Level7){L7S = 0;}
                if(Level8){L8S = 0;}
                if(Level9){L9S = 0;}
                if(Level10){L10S = 0;}
                if(Level11){L11S = 0;}
                if(Level12){L12S = 0;}
                if(Level13){L13S = 0;}
                if(Level14){L14S = 0;}
                if(Level15){L15S = 0;}
                if(Level16){L16S = 0;}
                if(Level17){L17S = 0;}
                if(Level18){L18S = 0;}
                linePOS = 0;
                restart += 1;
                endClick = true;
                speedX = 0;
                speedY = 0;
                textDiminish = 255;
                delayTimer = 0;
                underGround = false;
            }
        }
        if (!titleScreen && !endGame) {
        if (restart > 0) {
            text(restart, 35, dY + 23);
        }
        textSize(12);
        text("Hole " + (LevelSelect + 1), 45, dY + 18);
        text("Par  " + Par[LevelSelect], 280, dY + 18);
        text("Strokes " + LS[LevelSelect], 330, dY + 18);
        }
    noFill();
    stroke(100);
    strokeWeight(2);
    rect(15, dY - 70, 306, 60);
    line(15, dY - 40, 321, dY - 40);
    stroke(100);
    rect(362, dY - 70, 30, 30);
    for(var lRep = 32; lRep < 311; lRep += 17) {
        line(lRep, dY - 70, lRep, dY - 11);
    }
    textSize(18);
    fill(75);
    textAlign(CENTER, BOTTOM);
    text(ParSum[LevelSelect], 336, dY - 15);
    text(LST, 336, dY - 45);
    text(LST - ParSum[LevelSelect],  377, dY - 45);
    textAlign(LEFT, BOTTOM);
    for(var sRep = 0; sRep < 18; sRep += 1) {
        if (LevelSelect === sRep) {
            fill(255, 0, 0);
        } else {
            fill(75);
        }
        if (LS[sRep] > 0) {
            text(LS[sRep], 19 + sRep * 17, dY - 45);
        }
        fill(75);
        if (LevelSelect >= sRep) {
                text(Par[sRep], 19 + sRep * 17, dY - 15);
        }
        textSize(9);
        text(sRep + 1, 19 + sRep * 17, dY - 70);
        textSize(18);
    }
    noFill();
    stroke(255, 0, 0);
    rect(15 + LevelSelect * 17, dY - 70, 17, 60);
    stroke(0, 0, 255);
    rect(321, dY - 70, 30, 60);
    line(321, dY - 40, 350, dY - 40);
    fill(75);
    textSize(9);
    translate(12, dY - 32);
    rotate(-90);
        text("STROKES", 0, 0);
        text("PAR", -23, 0);
    resetMatrix();
    text("SCORE", 361, dY - 28);
    strokeWeight(1);
    textSize(13);
    
    //AutoComplete + Hole in 0
    var PrevAutoComplete = AutoComplete;
    if (keys[17] && keys[65] && !AutoComplete && !AConoff) {
            AutoComplete = true;
    }
    if (keys[17] && keys[65] && AutoComplete && AConoff) {
        AutoComplete = false;
    }
    if (AutoComplete && !keyIsPressed) {
        AConoff = true;
    }
    if (!AutoComplete && !keyIsPressed) {
        AConoff = false;
    }
    if (AutoComplete) {
        ballPOSx = holePOSx;
        ballPOSy = holePOSy;
        drop = false;
        UsedCommands = true;
    }
    if (keys[17] && keys[48]) {
        ballPOSx = holePOSx;
        ballPOSy = holePOSy;
        drop = false;
        alertText = "Hole in 0";
        textDiminishB = 255;
        UsedCommands = true;
    }
    if (AutoComplete && !PrevAutoComplete) {
        alertText = "AutoComplete ON";
        textDiminishB = 255;
    }
    if (!AutoComplete && PrevAutoComplete) {
        alertText = "AutoComplete OFF";
        textDiminishB = 255;
    }
    fill(255, 255, 255, textDiminishB);
    text(alertText, 20, 380);
    if (textDiminishB > 0) {
        textDiminishB -= 5;
    }
    
    //Slopes
    if (slopeLEFT) {
        slopeRIGHT = false;
        if (speedX > 0 && !shotLEFT) {
            speedX -= 0.3;
            if (speedX <= 1) {
                shotLEFT = true;
            }
        }
        if (shotLEFT) {
            speedX += grav/8; 
            if (grav < 20) {
                grav *= 1.05;
            }
        }
        slopeX = true;
    }
    if (slopeRIGHT) {
        slopeLEFT = false;
        if (speedX > 0 && shotLEFT) {
            speedX -= 0.3;
            if (speedX <= 1) {
                shotLEFT = false;
            }
        }
        if (!shotLEFT) {
            speedX += grav/8; 
            if (grav < 20) {
                grav *= 1.05;
            }
        }
        slopeX = true;
    }
    if (slopeUP) {
        slopeDOWN = false;
        if (speedY > 0 && !shotUP) {
            speedY -= 0.3;
            if (speedY <= 1) {
                shotUP = true;
            }
        }
        if (shotUP) {
            speedY += grav/8; 
            if (grav < 20) {
                grav *= 1.05;
            }
        }
        slopeY = true;
    }
    if (slopeDOWN) {
        slopeUP = false;
        if (speedY > 0 && shotUP) {
            speedY -= 0.3;
            if (speedY <= 1) {
                shotUP = false;
            }
        }
        if (!shotUP) {
            speedY += grav/8; 
            if (grav < 20) {
                grav *= 1.05;
            }
        }
        slopeY = true;
    }
    if (!slopeX && !slopeY) {
        grav = 1;
    }
    if (!PrevSlopeX && slopeX) {
        grav = 1;
    }
    if (!PrevSlopeY && slopeY) {
        grav = 1;
    }
    if (!slopeX) {
        slopeLEFT = false;
        slopeRIGHT = false;
    }
    if (!slopeY) {
        slopeUP = false;
        slopeDOWN = false;
    }
    if (underGround && Level18  && selection !== 15) {
        if (PrevSpeedX < speedX) {
            speedX = PrevSpeedX;
        }
    }
    PrevSlopeX = slopeX;
    PrevSlopeY = slopeY;
    PrevSpeedX = speedX;
    PrevSpeedY = speedY;
    oldX = ballPOSx;
    oldY = ballPOSy;
    
    var tipString = [
    "If you're backed up against a wall and can't draw\nback far enough, aim the other way for a rebound.", "Slope affects your ball's speed. If the hole is at the top of\na slope, draw farther back to get the necessary extra power\nand get your ball up the hill.", 
    "Use the walls to your advantage. If there is no straight\nshot, go for the rebound and try for the hole in one.", 
    "If you are having trouble with a hole, try short, controlled\nshots to get to the hole, then restart the hole and see if you\ncan replicate that with fewer putts.", 
    "Put your mouse over the score card a the top of\nthe screen to check your progress while you play.", 
    "Don't go into bunkers; they stop your ball almost immediately\nand are very difficult to get out of. Treat them with caution.",
    "Slopes can come in handy when trying to get the ball\naround a corner, but they can also slow the ball down or\nsend it backwards, so aim carefully.", 
    "Water will reset your ball without resetting\nyour strokes, so avoid it at all costs."
];
    
    
    if (titleScreen) {
        pushMatrix();
        var splashText = "8000+ Votes!";
        var splashFill = color(200 - sin(frameCount) * 55, 200 + cos(frameCount) * 55, 200 + sin(frameCount) * 55);
        textAlign(LEFT, CENTER);
        textSize(25);
        var splashPart = "";
        translate(300, 40);
        for (var i = 0; i < splashText.length; i ++) {
            fill(0, 0, 0, 100);
            text(splashText[i], -textWidth(splashText)/2 + textWidth(splashPart) + 3, 2);
            var sF = cos(frameCount * 8 - i * 20) * 40;
            fill(red(splashFill) + sF, green(splashFill) + sF, blue(splashFill) + sF);
            text(splashText[i], -textWidth(splashText)/2 + textWidth(splashPart), 0);
            splashPart += splashText[i];
        }
        popMatrix();
        resetShot = false;
        if (mouseX > 170 && mouseX < 230 && mouseY >= 323 + tS && mouseY <= 335 + tS && titleScreen) {
            if (!tipDisplay) {
                tipSelect = round(random(-0.49, tipString.length - 0.51));
            }
            tipDisplay = true;
        }
        if (tipDisplay && tY < 30) {
            tY += 8;
        }
        if (mouseY < 283 + tS) {
            tY = 0;
            tipDisplay = false;
        }
        if (mouseY > 370 + tS) {
            tY = 0;
            tipDisplay = false;
        }
        stroke(125);
        fill(185);
        quad(170, 323 + tS + tY, 182, 330 + tS + tY, 218, 330 + tS + tY, 230, 323 + tS + tY);
        noStroke();
        rect(50, 258 + tS + tY, 300, 65);
        fill(175);
        quad(50, 258 + tS + tY, 55, 263 + tS + tY, 55, 318 + tS + tY, 50, 323 + tS + tY);
        quad(350, 258 + tS + tY, 345, 263 + tS + tY, 345, 318 + tS + tY, 350, 323 + tS + tY);
        fill(200);
        quad(50, 258 + tS + tY, 55, 263 + tS + tY, 345, 263 + tS + tY, 350, 258 + tS + tY);
        quad(50, 323 + tS + tY, 55, 318 + tS + tY, 345, 318 + tS + tY, 350, 323 + tS + tY);
        textAlign(CENTER, CENTER);
        textSize(10);
        fill(0);
        text(tipString[tipSelect], 200, 290 + tS + tY);
        
        
        
        fill(30, 168, 2);
        strokeWeight(5);
        stroke(173, 116, 2);
        rect(50, 80 - tS - tY, 300, 240 + tS * 2);
        fill(130, 83, 3);
        strokeWeight(4);
        stroke(59, 39, 11);
        rect(155, 160 - tS - tY, 90, 30);
        rect(135, 200 - tS - tY, 55, 30);
        rect(210, 200 - tS - tY, 50, 30);
        fill(41, 23, 0);
        textSize(52); 
        text("MINI PUTT", 200, 120 - tS - tY);
        textSize(54);
        fill(122, 82, 1);
        text("MINI PUTT", 200, 120 - tS - tY);
        fill(255);
        textSize(56);
        text("MINI PUTT", 200, 120 - tS - tY);
        textAlign(LEFT, BOTTOM);
        textSize(12);
        fill(168, 113, 2);
        text("Version 1.0.3", 5, 395);
        text("by Matt", 350, 395);
        textAlign(CENTER, CENTER);
        if (mouseX >= 155 && mouseX <= 245 && mouseY >= 160 - tS - tY && mouseY <= 190 - tS - tY) {
            if (mouseIsPressed && !endClick) {
                titleScreen = false;
                Level1 = true;
                endClick = true;
                drop = true;
            }
            fill(255);
        } else {
            fill(179, 135, 69);
        }
        textSize(19);
        text("START", 191, 175 - tS - tY);
        noStroke();
        triangle(227, 168 - tS - tY, 240, 175 - tS - tY, 227, 182 - tS - tY);
        fill(179, 135, 69);
        text("TIPS", 162, 215 - tS - tY);
        if (mouseX >= 198 && mouseX <= 205 && mouseY >= 208 - tS - tY && mouseY <= 227 - tS - tY) {
            fill(255);
            if (mouseIsPressed && !endClick) {
                if(tips&&!endClick){onoffString="OFF";tips=false;endClick=true;}
                if(!tips&&!endClick){onoffString="ON";tips=true;endClick=true;}
                endClick = true;
            }
        } else {
            fill(130, 83, 3);
        }
        triangle(205, 207 - tS - tY, 205, 222 - tS - tY, 198, 215 - tS - tY);
        if (mouseX >= 265 && mouseX <= 272 && mouseY >= 208 - tS && mouseY <= 227 - tS - tY) {
            fill(255);
            if (mouseIsPressed && !endClick) {
                if(tips&&!endClick){onoffString="OFF";tips=false;endClick=true;}
                if(!tips&&!endClick){onoffString="ON";tips=true;endClick=true;}
                endClick = true;
            }
        } else {
            fill(130, 83, 3);
        }
        triangle(265, 207 - tS - tY, 265, 222 - tS - tY, 272, 215 - tS - tY);
        fill(255);
        text(onoffString, 235, 215 - tS - tY);
        var code = [1, 4, 5];
        var codeArray = [a, b, c];
        if (!LevelMenu) {
        for (var sRep = 0; sRep < 3; sRep += 1) {
            fill(130, 83, 3);
            stroke(59, 39, 11);
            rect(127 + sRep * 60, 255 - tY, 25, 25);
            noStroke();
            if (mouseX >= 115 + sRep * 60 && mouseX <= 122 + sRep * 60 && mouseY >= 260 - tY && mouseY <= 275 - tY) {
                fill(255);
                if (mouseIsPressed && !endClick) {
                    endClick = true;
                if(sRep===0){if(a>0){a-=1;}else{a=9;}}
                if(sRep===1){if(b>0){b-=1;}else{b=9;}}
                if(sRep===2){if(c>0){c-=1;}else{c=9;}}
                }
            } else {
                fill(130, 83, 3);
            }
            triangle(122 + sRep * 60, 260 - tY, 122 + sRep * 60, 275 - tY, 115 + sRep * 60, 268 - tY);
            if (mouseX >= 157 + sRep * 60 && mouseX <= 164 + sRep * 60 && mouseY >= 260 - tY && mouseY <= 275 - tY) {
                fill(255);
                if (mouseIsPressed && !endClick) {
                    endClick = true;
                if(sRep===0){if(a<9){a+=1;}else{a=0;}}
                if(sRep===1){if(b<9){b+=1;}else{b=0;}}
                if(sRep===2){if(c<9){c+=1;}else{c=0;}}
                }
            } else {
                fill(130, 83, 3);
            }
            triangle(157 + sRep * 60, 260 - tY, 157 + sRep * 60, 275 - tY, 164 + sRep * 60, 268 - tY);
        }
        fill(255);
        text(a, 139, 268 - tY);
        text(b, 199, 268 - tY);
        text(c, 259, 268 - tY);
        fill(130, 83, 3);
        stroke(59, 39, 11);
        rect(162, 288 - tY, 76, 30);
        if (mouseX >= 162 && mouseX <= 238 && mouseY >= 288 - tY && mouseY <= 318 - tY) {
            fill(255);
            if (a === code[0] && b === code[1] && c === code[2] && mouseIsPressed && !endClick) {
                LevelMenu = true;
                endClick = true;
                tS = 35;
            }
        } else {
            fill(179, 135, 69);
        }
        text("ENTER", 200, 302 - tY);
        fill(130, 83, 3);
        textSize(12);
        text("Unlock Level Select", 200, 244 - tY);
        } else {
            for (var lRep = 0; lRep < 3; lRep += 1) {
            for (var mRep = 0; mRep < 6; mRep += 1) {
                fill(130, 83, 3);
                stroke(59, 39, 11);
                rect(60 + mRep * 50, 215 + lRep * 50 - tY, 30, 30);
                if (mouseX >= 60 + mRep * 50 && mouseX <= 90 + mRep * 50 && mouseY >= 215 + lRep * 50 - tY && mouseY <= 245 + lRep * 50 + tY) {
                    fill(255);
                    if (mouseIsPressed && !endClick) {
if(mRep+1+lRep*6===1){Level1=true;LevelSelect=0;}
if(mRep+1+lRep*6===2){Level2=true;LevelSelect=1;}
if(mRep+1+lRep*6===3){Level3=true;LevelSelect=2;}
if(mRep+1+lRep*6===4){Level4=true;LevelSelect=3;}
if(mRep+1+lRep*6===5){Level5=true;LevelSelect=4;}
if(mRep+1+lRep*6===6){Level6=true;LevelSelect=5;}
if(mRep+1+lRep*6===7){Level7=true;LevelSelect=6;}
if(mRep+1+lRep*6===8){Level8=true;LevelSelect=7;}
if(mRep+1+lRep*6===9){Level9=true;LevelSelect=8;}
if(mRep+1+lRep*6===10){Level10=true;LevelSelect=9;}
if(mRep+1+lRep*6===11){Level11=true;LevelSelect=10;}
if(mRep+1+lRep*6===12){Level12=true;LevelSelect=11;}
if(mRep+1+lRep*6===13){Level13=true;LevelSelect=12;}
if(mRep+1+lRep*6===14){Level14=true;LevelSelect=13;}
if(mRep+1+lRep*6===15){Level15=true;LevelSelect=14;}
if(mRep+1+lRep*6===16){Level16=true;LevelSelect=15;}
if(mRep+1+lRep*6===17){Level17=true;LevelSelect=16;}
if(mRep+1+lRep*6===18){Level18=true;LevelSelect=17;}
                        endClick = true;
                        titleScreen = false;
                    }
                } else {
                    fill(179, 135, 69);
                }
                text(mRep + 1 + lRep * 6, 75 + mRep * 50, 230 + lRep * 50 - tY);
            }
        }
        
        }
    }
    if (endGame) {
        resetShot = false;
        textAlign(CENTER, CENTER);
        fill(30, 168, 2);
        strokeWeight(5);
        stroke(173, 116, 2);
        rect(50, 80, 300, 240);
        fill(130, 83, 3);
        strokeWeight(4);
        stroke(59, 39, 11);
        rect(100, 92, 200, 50);
        rect(100, 150, 200, 110);
        textSize(12);
        text("The code to unlock\nLevel Select is (1, 4, 5).", 200, 280);
        textSize(10);
        text("(Please don't give away the code to other users.)", 200, 302);
        fill(255);
        textSize(35);
        text("Game Over", 200, 115);
        textSize(20);
        if (!UsedCommands) {
        text("Bonus =  " + Bonus, 200, 170);
        text("Score =  " + (LST - ParSum[LevelSelect] + Bonus), 200, 205);
        text("Restarts =  " + restart, 200, 240);
        } else {
            text("No Score; Used Commands", 200, 200);
        }
        if (textDiminish > 0) {
            textDiminish -= 10;
        } else {
            textDiminish = 255;
        }
        if (dY === 0) {
            fill(255, 255, 0, textDiminish);
            textSize(12);
            text("^Score Card^", 200, 15);
        }
        textAlign(BOTTOM, LEFT);
    }
    if (!mouseIsPressed) {
        endClick = false;
    }
};
