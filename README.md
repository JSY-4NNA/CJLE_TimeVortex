Time Vortex: An Interactive History Education Application

Planning Miro Flowchart: https://miro.com/app/board/uXjVHV9OxbM=/?share_link_id=925348437456

An interactive, text-based history application built from scratch using Python, Pygame, and Pillow. This software is designed for intermediate students, shifting traditional historical learning from passive memorization into active, conditional branching logic puzzles.

Technical Highlights & Architecture

1. Custom Animation Pipeline (`load_gif`)
   Problem: Pygame's native image loader cannot process animated GIF files natively; it loads only the first frame and freezes.
   Solution: Integrated the `Pillow` library to programmatically parse individual frames (`gif.seek()`), convert pixel data matrices into an RGBA byte-string sequence to maintain transparency, and scale them dynamically into cacheable Pygame surfaces.

2. Memory Cache Optimization (Startup Preloading)
   To eliminate micro-stutters, framework lag, and file-access dropouts during active gameplay, all 49 heavy animated assets are pre-rendered and preloaded into a global dictionary storage layer (`ALL_GIFS`) at application startup. Screen swaps are entirely instantaneous.

3. Global State Management (`go_to`)
   Engineered an efficient state-handler that executes global scene transitions in just 5 lines of code. It programmatically flushes active frame indexes, clears time tracking thresholds, and re-routes active arrays instantly, avoiding repetitive and messy logic blocks.

4. Fault-Tolerant Asset Pipeline (`try/except`)
   The entire asset loading loop is wrapped inside explicit Python exception traps. If a graphical component is missing, corrupted, or unreadable, the system catches the error, alerts the console with a debugging code, and allows the core program to run safely without throwing a fatal crash.

5. Interface Coordinate Resolution (`pygame.Rect`)
   UI assets were constructed dynamically inside Canva. To resolve coordinate grid conflicts between Canva's canvas layout and Pygame's pixel matrix, a custom terminal logging utility was utilized to track structural cursor values and manually map out over 30 collision bounding-boxes.

Future Scalability & Improvements

Data Decoupling via JSON Engine: Future iterations will transition all historical dialogue narratives, quiz prompts, and conditional routing criteria out of the core Python engine and into external `.json` configuration models. This will allow non-technical educators to scale out and deploy custom history modules seamlessly without modifying the underlying source files.
Viewport for Precision in Graphics/Sprites: Implementing dynamic vector scaling algorithms to map pixel coordinate fields linearly across non-standard monitor resolutions while preserving canvas asset aspect ratios.

Requirements & Execution

To run the program, type:
**python3 TimeVortexGAME** into your terminal/console
Ensure you have Python 3 or Python shell installed alongside thes libraries before you run the game:

```bash
pip install pygame pillow
python main.py
