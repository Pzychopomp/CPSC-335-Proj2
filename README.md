# Project 2: Dynamic vs. Exhaustive - Crane unloading problem
## CPSC 335 - Algorithm Engineering
## Spring 2023
## Instructor: Himani Tawade
## Members:
 David Nguyen (dnguyen271@csu.fullerton.edu) & Vivian Truong(vtruong72@csu.fullerton.edu)

**along with a document with required details mentioned at the last, a demo video, readme file and .gitignore file. Submission will be a git repo link with all the requirements updated to repo on canvas.**



## The Exhaustive Optimization Algorithm Pseudocode:
    
    function crane_unloading_exhaustive(setting):
      if setting has no rows or columns:
          return "Error: Input setting must not be empty."
      max_steps = setting.rows() + setting.columns() - 2
      if max_steps >= 64:
          return "Error: Maximum number of steps is too large."
      best = new path object with input setting
      for steps from 1 to max_steps:
          mask = 1 << steps
          for bits from 0 to mask - 1:
              candidate = new path object with input setting
              valid = true
              for k from 0 to steps - 1:
                  bit = (bits >> k) & 1
                  if bit == 1:
                      if candidate.is_step_valid(STEP_DIRECTION_EAST):
                          candidate.add_step(STEP_DIRECTION_EAST)
                      else:
                          valid = false
                  else:
                      if candidate.is_step_valid(STEP_DIRECTION_SOUTH):
                          candidate.add_step(STEP_DIRECTION_SOUTH)
                      else:
                          valid = false
                  if valid and candidate.total_cranes() > best.total_cranes():
                      best = copy of candidate
    return best

## The Dynamic Programming Algorithm Pseudocode:

    

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



