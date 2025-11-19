🚀 Asteroids — Python Game Engine Project








A fully object-oriented, vector-based recreation of the classic Asteroids arcade game built with Python + Pygame — featuring smooth delta-time physics, procedural asteroid spawning, collision detection, projectile mechanics, and a modular game architecture designed for extensibility.

This project was developed as part of the Boot.dev Game Development track, and has since been upgraded with cleaner architecture, logging, and engine-style abstractions.

🎮 Demo

(Optional: I can generate a GIF preview for you — just ask.)

⭐ Features
🛸 Player Ship

Vector-based rotation using pygame.Vector2.rotate()

Smooth movement with acceleration via delta time

Custom triangular rendering using manual geometry

Shooting system with velocity inheritance

Built-in cooldown to regulate fire rate

☄️ Asteroids

Procedurally spawned from all four screen edges

Random velocity vectors + rotation offset

Three asteroid sizes — large → medium → small

Recursive splitting system with speed scaling

Collision detection based on circle radii

🔫 Shots / Bullets

Inherit directional velocity from ship rotation

Managed by a global shots sprite group

Auto-kill when off-screen (planned)

🧩 Engine Architecture

This project uses a semi-engine approach:

System	Purpose
CircleShape base class	shared position/velocity/radius logic
Sprite Groups	unified update/draw pipelines
AsteroidField spawner	timed procedural generation
Logger system	state+event tracking for debugging/tests

Sprite groups behave like subsystems:

updatable — everything that updates each frame

drawable — everything rendered each frame

asteroids — only asteroid instances

shots — player bullets

player — single instance (but could extend)

🧠 Architecture Overview
                ┌─────────────────────┐
                │       main.py       │
                └──────────┬──────────┘
                           │
          ┌────────────────┴────────────────┐
          v                                 v
 ┌─────────────────┐               ┌───────────────────┐
 │   Player.py      │               │ AsteroidField.py │
 └───────┬──────────┘               └─────────┬────────┘
         │                                    │
         v                                    v
 ┌─────────────────┐               ┌───────────────────┐
 │    Shot.py       │               │   Asteroid.py     │
 └───────┬──────────┘               └─────────┬────────┘
         │                                    │
         └──────────→ CircleShape.py ←────────┘

⚙️ Technical Highlights
🎯 Delta-Time Movement

Ensures framerate-independent physics:

self.position += self.velocity * dt

🌀 Procedural Asteroid Splitting
angle = random.uniform(20, 50)
v1 = self.velocity.rotate(angle) * 1.2
v2 = self.velocity.rotate(-angle) * 1.2

🎯 Collision Detection

O(1) vector distance check:

return self.position.distance_to(other.position) < (self.radius + other.radius)

📡 Logging System

Automatic logging into .jsonl streams:

log_state() → game state snapshots

log_event() → collisions, splits, shots fired

Useful for debugging or analytics.

📦 Installation
1️⃣ Clone repo
git clone https://github.com/YourUsername/asteroids.git
cd asteroids

2️⃣ Create virtual environment
python3 -m venv venv
source venv/bin/activate      # Linux/Mac
venv\Scripts\activate         # Windows

3️⃣ Install dependencies
pip install -r requirements.txt


Or manually:

pip install pygame

▶️ Run the Game
python3 main.py

🎮 Controls
Key	Action
W	Move forward
S	Move backward
A	Rotate left
D	Rotate right
Space	Shoot
Esc / Window X	Quit
🚧 Roadmap
🔜 Planned Improvements

Screen-wrap physics (like original Asteroids)

Object pooling for performance

Particle/explosion effects

Score system + UI overlay

Multiple levels or waves

Sound effects + background music

Better death animation & restart menu

Hit flash on collisions

🤝 Contributing

Contributions are welcome!
Open an issue or submit a pull request.

📝 License

This project is open-source and available under the MIT License.

🙌 Acknowledgments

Boot.dev for the game project framework

Pygame community for excellent documentation

Classic arcade games for inspiration
