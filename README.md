# Project 2: Dynamic vs. Exhaustive - Crane unloading problem
## CPSC 335 - Algorithm Engineering
## Spring 2023
## Instructor: Himani Tawade
## Members:
 David Nguyen (dnguyen271@csu.fullerton.edu) & Vivian Truong(vtruong72@csu.fullerton.edu)

**along with a document with required details mentioned at the last, a demo video, readme file and .gitignore file. Submission will be a git repo link with all the requirements updated to repo on canvas.**



## The Exhaustive Optimization Algorithm Pseudocode:
    
    def crane_unloading_exhasutive (setting):
          assert(setting.rows() > 0)
          assert(setting.columns() > 0)
          
          max_steps = setting.rows() + setting.columns() - 2
          assert(max_steps < 64)
          best = None
          
          for steps = 1 to max_steps inclusive:
              for bits = 0 to (2^steps) - 1 inclusive:
                  candidate = [start]
                  valid = true
                  for k = 0 to steps - 1 inclusive:
                      bit = (bit >> k) & 1
                      
                      if (bit == 1):
                          if (candidate.is_step_valid(STEP_DIRECTION_EAST):
                              candidate.add_step(STEP_DIRECTION_EAST):
                          else valid = false
                      else:
                          if (candidate.is_step_valid(STEP_DIRECTION_SOUTH):
                              candidate.add_step(STEP_DIRECTION_SOUTH)
                          else valid = false
                  endfor
              if (valid && (candidate.total_cranes() > best.total_cranes())):
                  best = candidate
              endfor
          endfor
## Exhaustive Optimization Scatterplot Graph

## The Dynamic Programming Algorithm Pseudocode:
    
    def crane_unloading_dyn_prog(setting):
    
        assert(setting.rows() > 0)
        assert (setting.columns > 0)
        A = (setting.rows(), vector<cell_type>(setting.columns()))
        A[0][0] = path(setting)
        assert(A[0][0].hash_value())
        
        for r = 0 to setting.rows() - 1:
            for c = 0 to setting.columns() - 1:
              if (setting.get(r, c) != CELL_BUILDING):
                  from_above = None
                  from_left = None
                  
                  if (r > 0 && A[r - 1][c].has_value()):
                      from_above = A[r -1][c]
                      
                  if (from_above->is_step_valid(STEP_DIRECTION_SOUTH):
                      from_above->add_step(STEP_DIRECTION_SOUTH)
                      
                  if (c > 0 && A[r][c - 1].has_value()):
                      from_left = A[r][c - 1]
                      
                  if (from_left->is_step_valid(STEP_DIRECTION_EAST)):
                      from_left->add_step(STEP_DIRECTION_EAST)
                      
                  if (from_above.has_value() && from_left.has_value()):
                      if (from_above->total_cranes() > from_left->total_cranes()):
                          A[r][c] = from_above
                      else: A[r][c] = from_left
                      
                  if (from_above.has_value() && !(from_left.has_value())):
                      A[r][c] = from_above
                      
                  if (from_left.has_value() && !(from_above.has_value())):
                      A[r][c] = from_left
                  endif
            endfor
        end for
        
        // Post-processing to find maximum-crane path
        best = A[0][0]
        assert(best->has_value())
        for r = 0 to setting.rows() - 1:
        for c = 0 to setting.columns() - 1:
        if (A[r][c].has_value() && A[r][c]->total_cranes() > (*best)->total_cranes()):
        best = &(A[r][c])
        assert(best->has_value())

        return **best
        
## Dynamic Programming Scatterplot Graph
    ![alt text](https://github.com/Pzychopomp/CPSC-335-Proj2/blob/main/ex%20plot.jpg) "Scatterplot")
# To Do:

# I. Create a Document with the following 
- Exhastive Algorithm Soltuion Psuedocode and time analysis
- Plot a graph for time vs input size for the algorthm
- Dynamic Algorithm Soltuion Psuedocode and time analysis
- Plot a graph for time vs input size for the algorthm
- Answer the below question based on the algorithm run time observations

Questions
1.	Is there a noticeable difference in the performance of the two algorithms? Which is faster, and by how much? Does this surprise you?

2.	Are your empirical analyses consistent with your mathematical analyses? Justify your answer.

3.	Is this evidence consistent or inconsistent with hypothesis 1? Justify your answer.

4.	Is this evidence consistent or inconsistent with hypothesis 2? Justify your answer.


# II. Create video demo for a running implementation format is same as Project 1


