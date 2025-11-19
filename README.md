Asteroids (Python + Pygame)

A fully object-oriented recreation of the classic Asteroids arcade game using Python and Pygame, featuring delta-time physics, procedural asteroid spawning, projectile mechanics, and a modular sprite-based architecture.

This project is part of my Boot.dev game-development learning path.

Features
🚀 Player Ship

Smooth rotation using pygame.Vector2.rotate()

Delta-time movement (consistent on any FPS)

Custom triangle rendering

Shooting system with cooldown

☄️ Asteroids

Procedurally spawned from all edges

Three asteroid sizes (large → medium → small)

Movement vectors randomized per spawn

Splits into smaller asteroids when hit

🔫 Shots

Fired in direction of ship's rotation

Move independently in straight lines

Managed in a dedicated sprite group

🧩 Architecture

CircleShape base class for shared logic

Sprite groups: updatable, drawable, asteroids, shots

Centralized logger for debugging & Boot.dev tests

Clean separation of responsibilities across modules

Project Structure
asteroids/
│
├── main.py
├── constants.py
├── logger.py
│
├── player.py
├── asteroid.py
├── asteroidfield.py
├── shot.py
│
└── circleshape.py

Controls
Key	Action
W	Move forward
S	Move backward
A	Rotate left
D	Rotate right
Space	Shoot
ESC or window X	Quit
Installation
1. Clone the repo
git clone https://github.com/<your-username>/asteroids.git
cd asteroids

2. Create virtual environment
python3 -m venv venv
source venv/bin/activate        # macOS/Linux
venv\Scripts\activate           # Windows

3. Install dependencies
pip install pygame

Running the Game
python main.py

Technical Highlights
Delta-Time Movement
self.position += self.velocity * dt

Collision Detection
return self.position.distance_to(other.position) < (self.radius + other.radius)

Asteroid Splitting
angle = random.uniform(20, 50)
v1 = self.velocity.rotate(angle) * 1.2
v2 = self.velocity.rotate(-angle) * 1.2

Future Enhancements

Screen wrapping (classic Asteroids behavior)

Player lives + score system

Explosion particle effects

Sound effects

Better UI / HUD overlay

Menu & restart screen

License

This project is licensed under the MIT License.

Notes

This project was built as part of my Python/Pygame learning progression. The architecture is intentionally modular so I can expand it with new systems (enemies, UI, animations), and so the project serves as a strong portfolio example.
