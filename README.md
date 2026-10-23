# GMU RoboSub AUV

Software, research notes, and hardware documentation for George Mason University's RoboSub team.

## Repository layout

| Folder | What goes there |
|--------|-----------------|
| `docs/research/` | Notes on technologies we are learning (one file per topic) |
| `docs/hardware/` | Setup steps, wiring, and gotchas for each piece of hardware |
| `docs/competition/` | RoboSub rules, tasks, and strategy notes |
| `docs/meeting-notes/` | Dated notes from team meetings |
| `experiments/` | Small standalone scripts to test one thing (a camera, a detector, a MAVLink message) |
| `ros2_ws/src/` | Vehicle code as ROS 2 packages (later on, once experiments work) |
| `scripts/` | Helper scripts (install, setup, launch) |
| `config/` | Parameter files, ArduSub parameter backups, calibration files |
| `models/` | Notes on trained models (large weight files are not committed) |

## Getting started

1. New to Git? Start with [docs/git-basics.md](docs/git-basics.md).
2. Read [CONTRIBUTING.md](CONTRIBUTING.md) for how we use branches and pull requests.
3. Clone the repo: `git clone <repo-url>`
4. Check the repo's **Issues** tab (our to-do list) for a task to take, or add notes to `docs/research/`.

## Roadmap

- [ ] Connect ZED 2i and webcam to the Jetson
- [ ] Talk to the Pixhawk from the Jetson over MAVLink (read heartbeat and telemetry)
- [ ] Install ROS 2 on the Jetson and publish camera images as a topic
- [ ] Detect a gate or colored target with OpenCV
- [ ] Send a movement command from ROS 2 to ArduSub
- [ ] Test in simulation before the pool
