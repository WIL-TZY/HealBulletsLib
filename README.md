## Heal Bullets Library by willowitzy & kachoow  

This library aims to recreate the green healing bullets from Undertale and Deltarune. It includes several bullets with healing properties featured in Deltarune. 

This library is designed for use in [Kristal](https://github.com/KristalTeam/Kristal).
  
## How to use  
  
1) Place this folder inside your mod's libraries folder.   
2) Set up an encounter with an enemy.  
3) Create a bullet file that inherits from HealBullet (set class as `HealBullet` instead of `Bullet`). Alternatively, you can use one of the example files from the library, `heal.lua` or `heal_candy.lua`, found in the `assets/sprites/bullets` directory.  
4) Decide the amount to heal by adding the `self.heal` variable in your bullet's init function. If no amount is set, it defaults to 1.  
5) Call the bullet inside a wave and then call the wave in your enemy file. You can use the `aiming_heal` example wave from the library. It should all work now :)  
  
This library is set to work independently of `targetSystem` being set to true or false. However, you can modify the `onHeal()` function to create various effects. For example, you can make the entire party heal when the soul collides with a heal bullet.   
  
**Note:**  
If you want to change the bullet's color, you can do so in the `getTypeColor()` function by returning an RGB color. The library defaults to green, similar to Undertale/Deltarune, but you can customize it to your needs. For example:
```lua 
if self.type == "red" then  
        return {255, 0, 0}  
elseif self.type == "green"  
	return {0, 255, 0}  
elseif self.type == "blue"  
	return {0, 0, 255}  
--and so on  
end  
```

Then, in your bullet's file, you can make the bullets switch colors by adding the following code in the `<BulletName>:init(x, y, dir, speed)` function:
```lua
function Heal:init(x, y, dir, speed)  
  
    local type = Utils.pick({ "red", "green", "blue" })  
    super.init(self, x, y, type, "bullets/bulletname")  
```
  
The bullets will now spawn with random colors based on the type you set up for them individually.
  
 
**Note:**  
The bullet will only be display correctly if you use white colored sprites. If the base color is not white, the blending may be affected and result in unwanted effects.

Feel free to make these adjustments and enjoy using the Heal Bullets Library!
