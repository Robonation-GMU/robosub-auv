# Contributing

This is a student team and most of us are learning as we go. Asking questions is expected. Breaking things on a branch is fine.

## The basic workflow

1. **Never commit straight to `main`.** `main` should always hold work that runs or notes that are accurate.
2. Create a branch for your work:
   ```
   git checkout main
   git pull
   git checkout -b yourname/short-description    # e.g. alex/zed-camera-test
   ```
3. Commit small, clear steps:
   ```
   git add <files>
   git commit -m "Add script that grabs frames from the ZED 2i"
   ```
4. Push and open a pull request (PR) on GitHub:
   ```
   git push -u origin yourname/short-description
   ```
5. Ask one teammate to review. Once approved, merge it.

## Where things go

- Learning something new? Copy `docs/research/_template.md` to `docs/research/<topic>.md`.
- Testing one piece of hardware or one library? Put a script in `experiments/<area>/`.
- Writing code the vehicle will actually run? It belongs in a ROS 2 package under `ros2_ws/src/`.
- Changed a hardware setting (ArduSub parameter, wiring)? Update the matching file in `docs/hardware/`.

## Rules of thumb

- **No personal and confidential info.** Passwords, logins, etc.
- **No large files.** Videos, datasets, rosbags, and model weights go in the team's shared onedrive. Put a link to it in a README instead.
- **Write down what you learn.** If something took you an hour to figure out, a short note saves the next person that hour.
- **Use issues for tasks.** If you find a problem or have an idea, open an issue so it nobody forgets it.

## Commit message style

Start with a verb, keep it under about 70 characters: `Add`, `Fix`, `Update`, `Document`, `Remove`.
