```mermaid
graph TD
    classDef default fill:#2d3436,stroke:#74b9ff,stroke-width:2px,color:#ffffff,font-family:Arial;
    classDef endNode fill:#00b894,stroke:#000000,stroke-width:2px,color:#ffffff;
    
    A[Data Acquisition] --> B[Data Preprocessing & Cleaning]
    B --> C[Feature Extraction]
    C --> D[Model Training & Hyperparameter Tuning]
    D --> E[Model Evaluation]
    
    E -.->|Refine Parameters| D
    E -.->|Adjust Features| C
    
    E -->|Validation Success| F[Deployment API & Flutter Integration]
    
    class F endNode;
