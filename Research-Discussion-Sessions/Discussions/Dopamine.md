# DOPAMINE: A RESEARCH FRAMEWORK FOR DEEP REINFORCEMENT LEARNING
Authors: Pablo Samuel Castro, Subhodeep Moitra, Carles Gelada, Saurabh Kumar & Marc G. Bellemare
Google Brain

Reference: {psc,smoitra,cgel,kumasaurabh,bellemare}@google.com

PDF: https://arxiv.org/pdf/1812.06110

Github: https://github.com/google/dopamine

Colab: https://colab.research.google.com/github/google/dopamine/blob/master/dopamine/colab/agents.ipynb#scrollTo=emUEZEvldNyX

Discussion Lead: [Laura Montoya](http://www.lauranmontoya.com)

Slides: [Dopamine Discussion Slides](./Slides/Dopamine.pdf)

Video: [Dopamine - AIDLE - AI Research Discussion](https://youtu.be/bd4CsDp00RA)

## Notes
- [ ] 1 Introduction
    - [ ] Deep Reinforcement Learning
        - [ ] Complex agent-environment interactions
            - [ ] An agent navigating a video game maze from vision
    - [ ] TensorFlow based
        - [ ] Composed of 12 Python Files
        - [ ] Emphasis on complex agent-environment interactions
    - [ ] Value Based Deep RL
        - [ ] Architecture Research
        - [ ] Comprehensive Studies
        - [ ] Visualizations
        - [ ] Algorithmic Research*
        - [ ] Instruction*
    - [ ] OpenAI Baseline for DRL - DQN (Deep Q-Network)
        - [ ] Complex - composed of 6 modules
        - [ ] DQN Innovative in use of agent architecture
            - [ ] Target network
            - [ ] Replay memory
            - [ ] Atari specific preprocessing
- [ ] 2 Software for DRL Research
    - [ ] Deep Learning Research
        - [ ] Significant Operations
            - [ ] Component Modularity
            - [ ] Automatic Differentiation
            - [ ] Visualization
        - [ ] Fundamental Research
        - [ ] Simulated Environments
            - [ ] Arcade learning environments (ALE)** 
                - [ ] Used by Dopamine
            - [ ] Continuous control
            - [ ] First Person environments
            - [ ] Real time strategy games
        - [ ] 2.1 The Deep Q-Network Architecture
            - [ ] Architecture Research
                - [ ] Interaction between components - including network topologies
                - [ ] Commonplace that an agent be composed of multiple interacting components*
            - [ ] Algorithmic Research
                - [ ] Improve underlying algorithms that drive learning and behavior in DRL
                - [ ] Not tied to specific agent architecture
                - [ ] Increase robustness of Q-learning
                    - [ ] Using double DQN & gap increasing methods
                        - [ ] Prioritize experience replay
                        - [ ] More frequently sample states with high prediction error
                        - [ ] Retrace - computes a sum of n-step returns, weighted by truncated correction ratio derived from policy probabilities
                        - [ ] Dueling algorithm - separates estimation of Q-values into advantage and baseline components
                        - [ ] Distributional methods - replace scalar made by DQN with a value distribution - introduces new losses to the algorithm  
            - [ ] Visualization
                - [ ] Concerned with gaining a deeper understanding of deep RL methods through focused interventions
                - [ ] Performance is not emphasized
                - [ ] Not restricted to visual analysis - although the majority of research completed focuses on visualizations
        - [ ] 2.2 Software Objectives
            - [ ] How is DRL Research enabled by software?
                - [ ] Existing code availability vs new code written
                - [ ] Shelf life of code written during research
                - [ ] Value of high performance code
                - [ ] Code Complexity
                    - [ ] Complex (large, modular, abstract) framework vs Simple (compact, monolithic, readily understood) framework
- [ ] 3 Dopamine
    - [ ] Design Principles
        - [ ] Self-contained and Compact
        - [ ] Reliable and reproducible
    - [ ] Self-contained and compact
        - [ ] Figure 1 
            - [ ] Lifecycle of an experiment 
            - [ ] 12 Files
            - [ ] 2000 lines of Python code
            - [ ] Main components
                - [ ] Runner Class
                    - [ ] Interactions between agent and ALE - Taking steps and receiving observations
                    - [ ] Booking - Checkpointing and logging
                - [ ] Checkpointer
                    - [ ] Regularly saving
                    - [ ] Learned weight reuse
                - [ ] Logger
                    - [ ] Saving statistics
                        - [ ] Accumulated training or evaluation rewards
                    - [ ] Stored in disk for visualization
                - [ ] Agent Classes
                    - [ ] Core logic for inference and learning
                    - [ ] Receives Atari 2600 frames from Runner
                    - [ ] Returns actions to perform
                    - [ ] Performs learning using replay memory
            - [ ] 4 Established Agents
                - [ ] DQN - base class for all agents
                - [ ] C51 - parameterization of rainbow agent
                - [ ] Rainbow agent - simplified single-GPU
                - [ ] IQN
        - [ ] Rainbow Agent Components (Dopamine)
            - [ ] N-step updates
            - [ ] Prioritized experience replay
            - [ ] Distributional reinforcement learning
            - [ ] *Does not include
                - [ ] Double DQN
                - [ ] Dueling architecture
                - [ ] Noisy Networks
        - [ ] Appendices B & C offer code examples of performance modifications
        - [ ] Gin-config Scheme (Figure 2)
            - [ ] Parameter Injection - changing default parameters dynamically
            - [ ] All parameters in a single file
    - [ ] 3.3 Baselines for Comparison
        - [ ] Uniform set of Hyper-parameters for all agents
        - [ ] Consistency over optimization
        - [ ] Facilitates hyperparameter exploration
        - [ ] Table 1 - Summary of Default vs Published Results
            - [ ] Minimal action set from ALE provided by Gym interface
        - [ ] Figure 3 - Space Invaders & Seaquest
            - [ ] 4 agents compared
            - [ ] Published vs Default settings
            - [ ] Of Note:
                - [ ] Seaquest - changing dynamics between algorithms in default vs published
- [ ] 4 Revisiting ALE: Test Case
        - [ ] Continue investigation by Machado et al.
            - [ ] Standard methodology for evaluating algorithms within ALE
            - [ ] Plotting DQN against C51 or Rainbow, but not both
        - [ ] 4.1 Episode Termination
            - [ ] “When human would stop playing”
                - [ ] Run out of lives
                - [ ] Finished game
            - [ ] Definitions
                - [ ] “Game Over” - termination condition
                - [ ] “Life Loss” - player losses life
                    - [ ] Artificial episode boundaries in replay memory
            - [ ] Gin-config option
                - [ ] AtariPreprocessing.terminal_on_life_loss = True
            - [ ] Figure 4
                - [ ] Difference in performance under 2 conditions
                - [ ] Life loss 
                    - [ ] improves performance in simpler games
                    - [ ] Hinders in complex games - agent cannot learn consequences of loss of life
                    - [ ] Disabled in default settings
        - [ ] 4.2 Measuring Training Data & Summarizing Learning Performance
            - [ ] Training Data
                - [ ] Game Frames experienced by agent
                - [ ] Each Iteration
                    - [ ] Fixed number of frames
                    - [ ] Rounded up to nearest episode boundary
            - [ ] Two Schedules for Running of Jobs
                - [ ] Train - measures average score during training
                - [ ] train_and_eval - includes evaluation runs where learning is stopped
            - [ ] Figure 5 
                - [ ] Difference in reported scores between training and evaluation
                - [ ] Little difference found
                - [ ] Restricting to training curves is sufficient
        - [ ] 4.3 Sticky Actions of Agent Performance
            - [ ] Original ALE
                - [ ] Rewards agents that can memorize sequences of actions to achieve high scores
            - [ ] ALE w/Sticky Actions
                - [ ] Stickiness parameter - 
                - [ ] probability that the environment will execute the agent’s previous action opposed to the one the agent just selected
                - [ ] Implements a form of action momentum
                - [ ] Gin-config option
                    - [ ] Runner.sticky_actions = False
            - [ ] Figure 6 - Sticky vs Non-sticky Actions
                - [ ] Enabled by default in Dopamine
                - [ ] Sticky actions usually reduce performance
                    - [ ] improve performance in some cases (Rainbow playing Space invaders)
    - [ ] 6 Conclusion
        - [ ] Single-GPU, value based agents, running on ALE
        - [ ] Future
            - [ ] Policy based methods
            - [ ] Other environments
            - [ ] Distributed methods
