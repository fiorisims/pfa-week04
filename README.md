# pfa-week04
Fiori Sims Week 4 Homework for Programming for Animators FA26 
Install Pygame, Install and run bounce_game.py through your computer's terminal. 
Created a simple ball game and changed the theme. Added objects to break/changed their shape and added projectiles. Changed ball/player shape into rocket 
def 1:
def damage_planet(self, planet):
        planet.hits += 1
        planet.flash = 0.12
        broken_now = planet.hits >= planet.max_hits
        self.shake = min(12.0, self.shake + (9.0 if broken_now else 3.0))
        if not broken_now:
            self.play(self.snd_hit)
            return
This def is the maximum/minimum hits needed to break the planets in the game. 
            
def 2:
    def collide(self, ball_pos, ball_r):
        """Overlap against the sphere as (outward normal, depth)."""
        off = ball_pos - self.pos
        dist = off.length()
        depth = ball_r + self.radius - dist
        if depth <= 0:
            return None, 0.0
        normal = off / dist if dist > 1e-6 else pygame.Vector2(0, -1)
        return normal, depth

This def decides how the ball will keep itself from overlapping with the other objects. The normal = off / dist if dist is the direction in which the objects are separated in. 
        
def 3:
    def lose_life(self):
        self.lives -= 1
        self.shake = 16.0
        self.meteors.clear()
        self.reset()
        self.invuln = INVULN
        self.play(self.snd_hurt)
        if self.lives <= 0:
            self.state = STATE_OVER
            self.banner = "GAME OVER"
            self.banner_time = 99.0

This def decides what information appears on the screen when the player loses. 

Self-written def:

