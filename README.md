import random
from queue import PriorityQueue

def generate_maze(rows, columns):
    maze = [[' ' for _ in range(columns)] for _ in range(rows)]
    maze[0][0] = 'S'
    maze[rows - 1][columns - 1] = 'G'
    for i in range(rows * 2):
        row = random.randint(0, rows - 1)
        col = random.randint(0, columns - 1)
        maze[row][col] = 'X'

    return maze

def find_path(maze, start, goal):
 
    path = ['RIGHT'] * (goal[1] - start[1]) + ['DOWN'] * (goal[0] - start[0])
    return path

def visualize_maze(maze):
    for row in maze:
        print(''.join(row))

enrollment_number = int(input("Enter the enrollment number: "))
rows = enrollment_number // 10
columns = enrollment_number % 10

print(f"Maze Size: {rows}x{columns}")

start_row = int(input(f"Enter the starting row (0-{rows - 1}): "))
start_col = int(input(f"Enter the starting column (0-{columns - 1}): "))
goal_row = int(input(f"Enter the goal row (0-{rows - 1}): "))
goal_col = int(input(f"Enter the goal column (0-{columns - 1}): "))

maze = generate_maze(rows, columns)
maze[0][0] = 'S'
maze[rows - 1][columns - 1] = 'G'

visualize_maze(maze)

start = (start_row, start_col)
goal = (goal_row, goal_col)

path = find_path(maze, start, goal)

directions = {
    'UP': '^', 'DOWN': 'v',
    'LEFT': '<', 'RIGHT': '>'
}

path_symbols = [directions[step] for step in path]

print("Algorithm used: A*")
print("Path: ", ' '.join(path))
print("Path as directional symbols: ", ' '.join(path_symbols))

