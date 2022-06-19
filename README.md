# 👻 Gimbal Ghost Default Gimbals
The default pre-rendered sticks and template for creating pre-rendered sticks in Gimbal Ghost.

The goal of this repo is to eventually provide users with a template to create their own gimbals for use in Gimbal Ghost. 

## 🕹️ How to Use
1. Open the `gimbal-model.blend` file within Blender.
1. Open the scripting text editor panel in Blender.
1. Load the `prerender.py` script in the scripting text editor panel.
1. Run the script from within Blender and wait for frames to be rendered to the `/frames` directory (this will take some time depending on your CPU).

## ⚙️ How It Works
Gimbal Ghost's rendering speed relies on a pre-rendered set of gimbal images that are generated using the code and models in this repo. Here is a high level overview:
* All possible stick positions for a single gimbal are pre-rendered using a Blender model and python script that interacts with the Blender model.
* The prerender script moves the gimbal in the x and y directions within a position range of -500 to 500 where center stick is represented by `(0, 0)`, upper right is `(500, 500)` and lower left if `(-500, -500)`.
* The prerender script then uses Blender to render a frame to an RBGA `.png` image file where the name of the file is the position of the stick in that frame, e.g. `-450_70.png`.
* To save on file space, the prerender script subsamples the posible stick positions only rendering an image for positions in increments of 10 (adjustable in script).
* Information about the prerendered stick frames is stored in a `gg-manifest.json` file which includes information about the image locations, x, y ranges and step size.

## 💻 Local Development
The following dependencies will be needed to develop locally:
* [Blender v2.83 LTS](https://www.blender.org/download/lts/2-93/)

## 📝 License
Licensed under GPLv3.

Gimbal and stick blender model modified from Bastian Sondermann's [Blackbox Sticks Exporter 3D](https://github.com/bsondermann/BlackboxSticksExporter3D).