# Heal Bullets Library by willowitzy & kachoow
This library is an attempt at recreating the green healing bullets from Undertale and Deltarune.   
Comes with a few bullets that were featured in Deltarune with healing properties.  
For [Kristal](https://github.com/KristalTeam/Kristal)  
  
## How to use  
  
1) Place this folder inside your mod's libraries folder.   
2) Create an encounter with an enemy all set up.   
3) Create a bullet file that inherits from HealBullet. (Set class as "HealBullet" instead of "Bullet"). Alternatively, you can use one of the pre-made files from the library, heal.lua or heal_candy.lua, found in the bullets folder.
4) Decide the amount to heal by adding self.heal variable in your bullet's init. If an amount isn't set, it defaults to 1.  
5) Call the bullet inside a wave and then call the wave in your enemy file. You can use the "aiming_heal" example wave from the library. It should all work now :)  
  
This library is set to work independently of having targetSystem set to true or false. But you can mess around with the onHeal() function to make all kinds of things. Like making the whole party heal when the soul collides with a heal bullet, for instance.   
  
OBS:  
If you want to change the bullet's color do it in getTypeColor() and return a RGB color. This library defaults it to green, like how it is in Undertale/Deltarune. But you can change it for your own needs.  
For example, you can do something like:  
if self.type == "red" then  
        return {255, 0, 0}  
if self.type == "green"  
	return {0, 255, 0}  
if self.type == "blue"  
	return {0, 0, 255}  
--and so on  
end  
  
And then you can make the bullets switch colors by this in your bullet's file:  
  
  
function Heal:init(x, y, dir, speed)  
  
    local type = Utils.pick({ "red", "green", "blue" })  
    super.init(self, x, y, type, "bullets/bulletname")  
  
And the bullets will spawn colored randomly according to the color you set up for its type inside MoveBullet.   
  