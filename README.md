```mermaid
graph TD
    classDef default fill:#2d3436,stroke:#74b9ff,stroke-width:2px,color:#ffffff,font-family:Arial;
    classDef endNode fill:#00b894,stroke:#000000,stroke-width:2px,color:#ffffff;
    
    A[Data Acquisition] --> B[EDA]
    B --> C[Data Preprocessing]
    C --> D[Feature Extraction]
    D --> E[Model Training & Hyperparameter Tuning]
    E --> F[Model Evaluation]
    
    F -.->|Refine Parameters| E
    F -.->|Adjust Features| D
    
    F -->|Validation Success| G[Deployment API & Flutter Integration]
    
    class G endNode;
