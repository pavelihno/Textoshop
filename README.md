# Textoshop: An intelligent text editor with interactions inspired by drawing software
<img src="demo.gif">

## [Online Demo](https://damienmasson.com/Textoshop) / [How to build](#how-to-build-and-run) / [Publication (CHI'25)](#publication)

Textoshop (*"Photoshop for text"*) is a system that explores how interactions inspired by drawing software can help edit text. For instance:
- Text can be **lengthened** or **shortened** by dragging its edges. Similarly, text can be **moved** around and **rotated** to change the order of the words.
- Tools help edit the text. For instance, the **smudge tool** can paraphrase a passage, the **eraser tool** can remove words while keeping the text coherent, and the **tone brush** can change the tone.
- A **tone picker** allows exploring thousands of tone nuances by navigating a 2D space.
- **Boolean operations** can be used to compose sentences by combining, intersecting,
or subtracting ideas or phrases.
- **Text layers** allow structuring, displaying, and editing text in independent views.

Under the hood, Textoshop uses a large language model (LLM) to power many of these interactions. For more details, see the accompanying [research paper](#publication).


## How to build and run
The code is written in TypeScript and uses React and Vite. You'll need Docker installed on your machine to run Textoshop. You can download it [here](https://www.docker.com/products/docker-desktop/).

### 1. Set up environment variables
First, create your environment file by copying the example:
```bash
cp .env.example .env
```

Edit the `.env` file and configure the following settings:
- Add your OpenAI API key (required): `VITE_OPENAI_API_KEY`
- Optionally adjust the AI models:
  - `VITE_OPENAI_RESIZER_MODEL` (for text resizing)
  - `VITE_OPENAI_CHAT_MODEL` (for chat interface and other operations)

### 2. Build the Docker image
```bash
docker build -t textoshop .
```

### 3. Run the container
```bash
docker run --name textoshop-container -p 5173:5173 -v $(pwd)/.env:/app/.env textoshop
```

The application will be available at http://localhost:5173

### 4. Managing the container
- To stop the container: `docker stop textoshop-container`
- To restart it later: `docker start textoshop-container`
- To view logs: `docker logs textoshop-container`


## How to use?
After configuring your OpenAI API key in the `.env` file, you can test Textoshop using the shortcuts or you can run the study.
Note that the system was tested and developed for recent versions of **Google Chrome** or **Mozilla Firefox**.


## How to get an OpenAI API key?
Because Textoshop relies on the OpenAI API, you will need a key to make it work. You will need an account properly configured, see [here](https://platform.openai.com/account/api-keys) for more info.
Your key is never stored and the application runs locally and sends requests to the OpenAI API only.


## Can I try without an API key?
The systen depends on the OpenAI API to work. If you enter an incorrect key, you will still be able to go through the study but executing prompts will yield an error.


## Where are the video tutorials?
From the launcher, you can start the study to see the exact ordering and video tutorials participants went through.
Alternatively, you can go in the ``public/videos`` to review all the video tutorials.

## Publication
> Damien Masson, Young-Ho Kim, and Fanny Chevalier. 2025. Textoshop: Interactions Inspired by Drawing Software to Facilitate Text Editing. In Proceedings of the 2025 CHI Conference on Human Factors in Computing Systems (CHI '25) [10.1145/3706598.3713862](https://doi.org/10.1145/3706598.3713862)


You can also find the paper on [arXiv](https://arxiv.org/abs/2409.17088).