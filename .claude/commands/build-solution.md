# Build Solution Orchestrator

This is the main entry point for turning a business problem into an evaluated solution.

## High-Level Flow

1. **Intake Phase**
   - Run Intake Builder + Adversarial Checker loop
   - Present reviewed Intake at natural Checkpoint 1

2. **Architecture Phase**
   - Run Architecture Builder + Adversarial Checker loop
   - Present architecture proposal at Checkpoint 2

3. **Building Phase**
   - Break into logical components
   - Apply Builder + Checker loop per major component
   - Provide progress updates + Checkpoint 3 after significant modules

4. **Evaluation Phase**
   - Comprehensive functional + adversarial evaluation
   - Present evaluation report at Checkpoint 4

5. **Final Handoff**
   - Package documentation and deployment guidance

The system automatically runs internal builder/checker loops and surfaces clean, reviewed outputs at natural decision points. The user provides direction at checkpoints.