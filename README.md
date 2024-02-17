# Furthest-Building-You-Can-Reach
You are given an integer array heights representing the heights of buildings, some bricks, and some ladders.  You start your journey from building 0 and move to the next building by possibly using bricks or ladders. 

class Solution:
    def furthestBuilding(self, heights: List[int], bricks: int, ladders: int) -> int:
        heap = []
        for i in range(len(heights) - 1):
            diff = heights[i + 1] - heights[i]
            if diff > 0:
                heapq.heappush(heap, diff)
                if len(heap) > ladders:
                    bricks -= heapq.heappop(heap)
                if bricks < 0:
                    return i
        return len(heights) - 1
