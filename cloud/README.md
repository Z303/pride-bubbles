# Pride Bubbles
![A dark blue background with a number of bubble in the pride flag colours from left to right](cloud.gif)

```
poke(0x3fc0+0,32)
poke(0x3fc0+1,64)
poke(0x3fc0+2,128)

poke(0x3fc0+36,0)
poke(0x3fc0+37,0)
poke(0x3fc0+38,0)

poke(0x3fc0+39,220)
poke(0x3fc0+40,220)
poke(0x3fc0+41,220)

poke(0x3fc0+42,255)
poke(0x3fc0+43,255)
poke(0x3fc0+44,255)

colours = {}
colours[1] = {r=228, g=3,   b=3}
colours[2] = {r=255, g=140, b=0}
colours[3] = {r=255, g=237, b=0}
colours[4] = {r=0  , g=128, b=38}
colours[5] = {r=0  , g=77 , b=255}
colours[6] = {r=117, g=7  , b=135}

for i=1, #colours do
	r=colours[i].r
	g=colours[i].g
	b=colours[i].b
	regnumber = 1 + i-1
	reg = 0x3fc0+regnumber*3
	poke(reg+0,r)
	poke(reg+1,g)
	poke(reg+2,b)
end

function TIC()
	cls()
	
 for i=1,#colours do
 	rect(0,22*(i-1)+2,240,22,i)
 end
  
 pts={}
 
 for i=1,15 do
  y=68+math.sin(-11+i*20)*10+ math.sin(i*30)*18
  x=114+math.sin(i*26)*80
  r=29+math.sin(i*20)*8+math.sin(i*10)*8
 	pts[#pts+1] ={x=x,y=y,r=r}
	end
	
	for i=1,20 do
  yoffset = math.sin(-11+i*20)*20+ math.sin(i*30)*28
  xoffset = math.sin(i*26)*80
  rsize = math.sin(i*20)*10 + math.sin(-11+i*10)*10
 	--pts[#pts+1] ={x=120+xoffset,y=64+yoffset,r=10+rsize}
	end
	
	
	table.sort(pts,function (a, b) 
		return a.r>b.r end)
 
 for i=1,#pts do 	
		circ(pts[i].x,pts[i].y,pts[i].r+2,15)
	end	
	
 for i=1,#pts do 
  circ(pts[i].x,pts[i].y,pts[i].r,13)	
		circ(pts[i].x,pts[i].y,pts[i].r-1,14)
	end		
end  
```