```mermaid
graph LR
    classDef client fill:#0984e3,stroke:#000000,stroke-width:2px,color:#ffffff;
    classDef api fill:#00b894,stroke:#000000,stroke-width:2px,color:#ffffff;
    classDef ml fill:#d63031,stroke:#000000,stroke-width:2px,color:#ffffff;
    classDef database fill:#fdcb6e,stroke:#000000,stroke-width:2px,color:#000000;

    subgraph Frontend [1. Client Layer - Flutter App]
        A[Mobile/Web UI]:::client
        B[Camera / Video Picker]:::client
        A --> B
    end

    subgraph Backend [2. API Layer - FastAPI/Flask]
        C[REST Endpoint POST /predict]:::api
        D[Request Validation & Error Handling]:::api
        C --> D
    end

    subgraph MLEngine [3. ML Core Engine]
        E[OpenCV: Frame Decoding]:::ml
        F[MediaPipe: Facial Landmarks Extraction]:::ml
        G[Feature Engineering: Blink Rate, PERCLOS...]:::ml
        H[StandardScaler Transform]:::ml
        I[XGBoost Classifier Model .pkl]:::ml
        
        E --> F --> G --> H --> I
    end

    subgraph Storage [4. Storage Layer]
        J[(Cloud Storage / S3)]:::database
        K[(Prediction Logs DB)]:::database
    end

    %% Connections between layers
    B -- "Send Video File (HTTP POST)" --> C
    D -- "Pass Video bytes" --> E
    I -- "Return JSON {status, confidence}" --> C
    C -- "Display Result" --> A
    
    %% Optional Storage Connections
    D -. "Save Video (Optional)" .-> J
    C -. "Log Result" .-> K
