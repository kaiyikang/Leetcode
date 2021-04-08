~~~python
class Solution:
    def findOrder(self, numCourses: int, prerequisites: List[List[int]]) -> List[int]:
        indegrees = [0 for _ in range(numCourses)]
        linjie = [[] for _ in range(numCourses)]

        for cur,pre in prerequisites:
            indegrees[cur] += 1
            linjie[pre].append(cur)

        queue = collections.deque()
        for i in range(len(indegrees)):
            if indegrees[i] == 0:
                queue.append(i)
        ret = []

        while queue:
            numCourses -= 1
            pre = queue.popleft()
            ret.append(pre)
            for cur in linjie[pre]:
                indegrees[cur] -= 1
                if indegrees[cur] == 0:
                    queue.append(cur)

        if numCourses!=0: return []
        
        return ret 
~~~

