# 🎮 TetrisJS 🎉

A **simple yet fun** Tetris game written entirely in **one file** — combining **HTML**, **CSS**, and **JavaScript**. This project is perfect for anyone who wants to dive into the basics of web-based game development, with clear inline comments to guide you through the code.

🚀 Just open the file in your browser and start playing Tetris right away! 🕹️

---

## 🛠 Features

- **Classic Tetris Gameplay**: Rotate, move, and drop Tetrominoes to clear rows and score points.
- **Minimalist Design**: Clean and simple UI.
- **Fully Functional in One File**: All the logic, styles, and visuals packed into a single `.html` file.
- **Responsive Controls**: Use arrow keys to control the game.
- **Lightweight and Fun**: No frameworks, no dependencies — just pure JavaScript magic! ✨

---

## 🚀 How to Play

1. **Open the Game**: Download or clone the repository and open `tetris.html` in any modern browser.
2. **Controls**:
   - ⬅️ **Left Arrow**: Move Tetromino left.
   - ➡️ **Right Arrow**: Move Tetromino right.
   - ⬆️ **Up Arrow**: Rotate Tetromino.
   - ⬇️ **Down Arrow**: Drop Tetromino faster.

3. **Objective**: Fill rows completely to clear them and score points. Keep the board as clear as possible to avoid game over!

---

## 📂 File Structure

```plaintext
tetris.html   // The only file you need! Includes HTML, CSS, and JavaScript.
```
---

## 🧰 Git Instructions

### Initializing a Repository

To upload or share this project on GitHub:

1. **Initialize Git**:
   ```bash
   git init
   ```
2. **Stage the File**:
   ```bash
   git add tetris.html
   ```
3. **Commit Your Changes**:
   ```bash
   git commit -m "Initial commit - TetrisJS"
   ```
4. **Add Remote Repository**:
   ```bash
   git remote add origin https://github.com/<your-username>/TetrisJS.git
   ```
5. **Push Your Code**:
   ```bash
   git branch -M main
   git push -u origin main
   ```

---

### Cloning the Repository

To clone the repository and play Tetris:

```bash
git clone https://github.com/<your-username>/TetrisJS.git
cd TetrisJS
```

Then, open `tetris.html` in your browser and start playing!

---

## 🛠 Troubleshooting

### Common Issue: Push Rejected (Remote Has Changes)
If you encounter a push error (e.g., `Updates were rejected because the remote contains work...`):

1. Pull the changes from the remote repository:
   ```bash
   git pull origin main --allow-unrelated-histories
   ```
2. Resolve any merge conflicts if necessary.
3. Push again:
   ```bash
   git push -u origin main
   ```

---

## 💡 What I Learned

- **Game Logic**: Handling Tetromino sequences, rotations, and collisions.
- **Canvas API**: Rendering the game board and Tetrominoes dynamically.
- **Randomization**: Generating random Tetromino sequences for gameplay.
- **Key Events**: Using `keydown` events for smooth and responsive controls.

---

## 📢 About the Creator

Built by **[@tairqaldy](https://github.com/tairqaldy)**, just for fun! 😄 This project is a quick dive into game development and pure JavaScript programming. Feel free to fork, share, or modify it to your heart’s content!

---

## 🎉 Let’s Play!

Clone the repository, open `tetris.html`, and enjoy the game! Happy coding and happy gaming! 🎮✨
```
