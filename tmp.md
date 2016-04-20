https://en.wikipedia.org/wiki/Connected_component_%28graph_theory%29

def dfs(m, i, j, visted, island):
    pass

def find_all_islands(m):
    islands = []
    visted = []
    for i in range(len(m)):
        for j in range(len(m)):
            island = []
            dfs[m, i, j, visted, island]
            if island:
                islands.append(island)
    return islands

if __name__ == '__main__':
    m = [
    ['A', 'B', 'D'],
    ['A', 'C', 'D'],
    ['C', 'D', 'D']
    ]
    print find_all_islands(m)
