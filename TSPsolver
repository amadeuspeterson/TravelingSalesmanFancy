    def fancy(self, time_allowance=60.0):
        results = {}
        upperbound = math.inf
        start_time = time.time()
        count = 0

        # This will run the greedy algorithm so that we can get an upperbound to prune our tree
        # Time complexity: O(n^2)
        # Space complexity: O(n)
        # while upperbound == math.inf:
        #     greedyResults = self.greedy()
        #     bssf = greedyResults['soln']
        #     upperbound = greedyResults['cost']
        randomResults = self.defaultRandomTour()
        bssf = randomResults['soln']
        upperbound = randomResults['cost']
        foundLesserPath = True

        while(foundLesserPath):
            foundLesserPath = False
            currRoute = copy.deepcopy(bssf.route)
            tempRoute = copy.deepcopy(currRoute)
            startingRoute = copy.deepcopy(currRoute)
            for i in range(len(currRoute) - 1):
                tempRoute = copy.deepcopy(startingRoute)
                tempRoute[i] = startingRoute[i + 1]
                tempRoute[i + 1] = startingRoute[i]
                solution = TSPSolution(tempRoute)
                if solution.cost < upperbound:
                    bssf = solution
                    count += 1
                    upperbound = bssf.cost
                    foundLesserPath = True
                    break

            tempRoute.clear()
            currRoute = bssf.route
            for i in range(len(currRoute) - 1, -1, -1):
                tempRoute.append(currRoute[i])
            solution = TSPSolution(tempRoute)
            if solution.cost < upperbound:
                bssf = solution
                upperbound = bssf.cost
                foundLesserPath = True


        end_time = time.time()
        results['cost'] = bssf.cost
        results['time'] = end_time - start_time
        results['count'] = 0
        results['soln'] = bssf
        results['max'] = 0
        results['total'] = count
        results['pruned'] = 0
        return results;
