#include<conio.h>
#include<graphics.h>
#include<stdlib.h>
#include<stdio.h>
#include<dos.h>

void start()
{
float octave[7] = {130.81, 146.83, 164.81, 174.61, 196, 220, 246.94};
setbkcolor(BLACK);
setcolor(RED);
setfillstyle(SOLID_FILL,RED);
circle(310,100,50);
floodfill(310,100,RED);
rectangle(355,80,380,120);
arc(387,125,0,100,30);
setcolor(WHITE);
settextstyle(DEFAULT_FONT,HORIZ_DIR,3);
outtextxy(280,90,"TNT");
putpixel(417,125,YELLOW);
putpixel(417,123,YELLOW);
putpixel(417,127,YELLOW);
putpixel(417,121,YELLOW);
putpixel(415,125,YELLOW);
putpixel(415,123,YELLOW);
putpixel(415,127,YELLOW);
putpixel(419,125,YELLOW);
putpixel(419,123,YELLOW);
putpixel(419,127,YELLOW);
putpixel(421,125,YELLOW);
putpixel(421,127,YELLOW);
putpixel(413,127,YELLOW);
putpixel(413,125,YELLOW);
rectangle(200,220,455,280);
setcolor(3);
settextstyle(DEFAULT_FONT,HORIZ_DIR,3);
	outtextxy(225,240,"BOMB DROP");
settextstyle(DEFAULT_FONT,HORIZ_DIR,1);
	outtextxy(420,440,"Developed by: BISHNU SUBEDI");
	while( !kbhit() )
	{
		sound( octave[ random(7) ]*4 );
		delay(300);
	}
	nosound();
getch();
clearviewport();
setcolor(RED);
setfillstyle(SOLID_FILL,RED);
circle(310,100,50);
floodfill(310,100,RED);
rectangle(355,80,380,120);
arc(387,125,0,100,30);
setcolor(WHITE);
settextstyle(DEFAULT_FONT,HORIZ_DIR,3);
outtextxy(280,90,"TNT");
putpixel(417,125,YELLOW);
putpixel(417,123,YELLOW);
putpixel(417,127,YELLOW);
putpixel(417,121,YELLOW);
putpixel(415,125,YELLOW);
putpixel(415,123,YELLOW);
putpixel(415,127,YELLOW);
putpixel(419,125,YELLOW);
putpixel(419,123,YELLOW);
putpixel(419,127,YELLOW);
putpixel(421,125,YELLOW);
putpixel(421,127,YELLOW);
putpixel(413,127,YELLOW);
putpixel(413,125,YELLOW);
rectangle(200,220,455,280);
setcolor(3);
settextstyle(DEFAULT_FONT,HORIZ_DIR,3);
outtextxy(225,240,"BOMB DROP");

settextstyle(DEFAULT_FONT,HORIZ_DIR,1);
outtextxy(420,440,"Developed by: BISHNU SUBEDI");

settextstyle(DEFAULT_FONT,HORIZ_DIR,2);
outtextxy(35,340,"Press any key to START the game..");

	while( !kbhit() )
	{
		sound( octave[ random(7) ]*4 );
		delay(300);
	}
	nosound();
	getch();
	clearviewport();

	rectangle(1,1,638,478);
	settextstyle(7,0,1);
	setusercharsize(50,30,50,30);
	setbkcolor(BLACK);
	settextstyle(DEFAULT_FONT,HORIZ_DIR,3);
	outtextxy(175,30,"HOW TO PLAY");

	setcolor(WHITE);
	settextstyle(3,0,1);
	setusercharsize(40,70,20,20);
	outtextxy(10,70,"1.Avoid the bomb from dropping on the ground.");
	outtextxy(10,110,"2.You can shoot the bomb in the air.");
	outtextxy(10,150,"3.Press SPACE to shoot the bomb.");
	outtextxy(10,190,"4.Press ARROW KEYS to move LEFT or RIGHT.");
	outtextxy(10,230,"5.For each hit on the bomb you get a score of 1.");
	outtextxy(10,270,"6.If a total of 5 bombs drop on the ground,the game is over.");
	settextstyle(7,0,2);
	sleep(0);
	settextstyle(DEFAULT_FONT,HORIZ_DIR,2);
	setcolor(YELLOW);
	outtextxy(130,430,"PRESS ANY KEY TO CONTINUE");
	getch();
	clearviewport();
	setbkcolor(BLACK);
	setcolor(4);
	settextstyle(DEFAULT_FONT,HORIZ_DIR,3);
	outtextxy(70,30,"WELCOME,Space Ranger!!");
	setcolor(3);
	settextstyle(DEFAULT_FONT,HORIZ_DIR,2);
	outtextxy(10,110,"You are hereby assigned the moral");
	outtextxy(10,150,"duty of saving our home planet.");
	outtextxy(10,190,"As you are the saviour, we put our");
	outtextxy(10,230,"total faith in you.");
	outtextxy(10,270,"But remember, few mistakes and its all");
	outtextxy(10,310,"over.");
	outtextxy(10,350,"Our planet, our only home is in your");
	outtextxy(10,390,"hands now.");
	getch();
	setusercharsize(1,1,1,1);
	settextstyle(0,0,0);
	setbkcolor(BLACK);
	clearviewport();
}

void blast(int s,int cs)
{
int e=5,i;
if(cs==0)
cs=1;
for(i=1;i<6;i++)
{
setfillstyle(1,12);
fillellipse(s*50+25,cs*25,e,5);
setfillstyle(i+1,i);
fillellipse(s*50+25,cs*25,5,e);
setfillstyle(6,3);
setcolor(YELLOW);
setfillstyle(SOLID_FILL,YELLOW);
circle(s*50+25,cs*25,20);
floodfill(s*50+25,cs*25,YELLOW);
floodfill(25,25,YELLOW);
delay(15);
sound(300);
e=e+5;
}
nosound();
}

void main()
{
int t;
char msg[128];
int gd=DETECT,gm;
int a,m,s,mus,i,hits,c[11],bm,score,mute,dly;
initgraph(&gd,&gm,"C:\\TurboC3\\BGI");
start();
restart:
clrscr();
cleardevice();
printf("\n\n\n\n\n\n\t\t\t\t\t\t\t\t\t  ");
s=1;mus=1;hits=0;bm=2;score=0;mute=1;dly=200;
for(i=0;i<11;i++)
c[i]=0;
randomize();
a=1;
con:
while(!kbhit())
{
a=random(10);
if(c[a]==0)

{
c[a]=1;
}
if(mute%2==0)
mus=random(1000);
else
{
mus=0;
nosound();
}
ep1:
cleardevice();
setbkcolor(BLACK);
setcolor(WHITE);
settextstyle(DEFAULT_FONT,HORIZ_DIR,1);
outtextxy(60,5,"Press Esc to exit                       Press Tab to pause ");
setfillstyle(0,1);
bar(50,15,550,480);
setfillstyle(1,9);
bar(s*50+20,360,s*50+30,400);
line(s*50+20,380,s*50+10,400);
line(s*50+30,380,s*50+40,400);
line(s*50+10,400,s*50+40,400);
line(s*50+20,360,s*50+25,350);
line(s*50+30,360,s*50+25,350);
setcolor(15);
rectangle(s*50+20,360,s*50+30,400);
rectangle(50,15,550,480);
setcolor(4);
if(mus!=0)
sound(mus);
setcolor(15);
setcolor(WHITE);
setfillstyle(SOLID_FILL,WHITE);
circle(300,790,370);
floodfill(300,730,WHITE);
setcolor(WHITE);
settextstyle(DEFAULT_FONT,HORIZ_DIR,2);
outtextxy(265,450,"EARTH");
setcolor(WHITE);
line(50,0,50,480);
line(550,0,550,480);
for(i=1;i<11;i++)
{
if(c[i]!=0)
{
setcolor(WHITE);
setfillstyle(1,4);
setcolor(RED);
setfillstyle(SOLID_FILL,RED);
rectangle(i*50+35,c[i]*25+16,i*50+45,c[i]*25+34);
setfillstyle(1,4);
fillellipse(i*50+25,c[i]*25+25,15,15);
setcolor(RED);
arc(i*50+45,c[i]*25+34,0,90,10);
setcolor(WHITE);
settextstyle(DEFAULT_FONT,HORIZ_DIR,1);
outtextxy(i*50+14,c[i]*25+22,"TNT");
if(bm!=0)
c[i]++;
}
if(c[i]==16)
{
blast(i,c[i]);
c[i]=0;
bm++;
}
}
if(bm==0)
{
delay(500);
goto ep2;
}
delay(dly);
if(mus!=0)
sound(mus+100);
if(dly==0)
dly=dly+2;
delay(dly+300);
	if(mus!=0)
sound(mus);
dly=dly-2;
if(bm==7)
{
bm=0;
goto ep1;
ep2:
cleardevice();
nosound();
setbkcolor(BLACK);
settextstyle(1,0,8);
setcolor(RED);
settextstyle(DEFAULT_FONT,HORIZ_DIR,4);
outtextxy(200,220,"GAME OVER");
setcolor(WHITE);
for(t=200;t<=1000;t=t+20)
{ sound(t);
delay(25); }
nosound();
sleep(1);
settextstyle(DEFAULT_FONT,HORIZ_DIR,2);
sprintf(msg," Your score is %d",score);
outtextxy(200,320,msg);
getch();
clearviewport();
scanb:
setcolor(YELLOW);
settextstyle(DEFAULT_FONT,HORIZ_DIR,2);
outtextxy(200,180,"Press R to restart");
outtextxy(200,200,"       or         ");
outtextxy(200,220,"Press ESC to exit ");
m=getch();
if(m==27)
exit(0);
if(m== 114|| m==82)
goto restart;
else
goto scanb;
}
}
m=getch();
if(m==0)
m=getch();
if(m==77)
{
if(s<10)
s++;
}
if(m==75)
{
if
(s>1)
s--;
}
if(m==32)
{
setcolor(4);
line(s*50+20,360,s*50+10,340);
line(s*50+30,360,s*50+40,340);
line(s*50+25,360,s*50+25,340);
blast(s,c[s]);
hits++;
if(c[s]!=0)
score++;
c[s]=0;
}
if(m==9)
getch();
if(m==13)
mute++;
if(m==27)
{
nosound();
exit(0);
}
goto con;
}

