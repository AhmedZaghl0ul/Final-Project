```mermaid
graph TD
    %% --- Modern Tech Color Palette ---
    classDef database fill:#2b3440,stroke:#3b82f6,stroke-width:2px,color:#e2e8f0;
    classDef process fill:#1e293b,stroke:#10b981,stroke-width:2px,color:#e2e8f0,rx:10px,ry:10px;
    classDef model fill:#312e81,stroke:#8b5cf6,stroke-width:2px,color:#e2e8f0;
    classDef highlight fill:#7c2d12,stroke:#f59e0b,stroke-width:2px,color:#e2e8f0;

    subgraph Phase 1: Data Preprocessing
        A[(Raw Videos: EmotiW 2023)]:::database --> B([Label Merging: Binary Classes]):::process
        B -. "Engaged (0) - Not-Engaged (1)" .-> C([Data Splitting: Train/Val/Test]):::process
    end

    subgraph Phase 2: Spatiotemporal Feature Extraction
        C --> D([Extract 30 Frames per Video]):::process
        D --> E([Detect Facial Landmarks]):::process
        E --> F(["Calculate Spatial Features"]):::process
        F --> G(["Aggregate Temporal Features"]):::process
        G --> H[(Exported Features CSV)]:::database
    end

    subgraph Phase 3: Model Architecture
        H --> I([StandardScaler: Normalization]):::process
        I --> J{"Classifier"}:::model
        J --> K(["Isotonic Calibration<br>Probability Scaling"]):::process
    end

    subgraph Phase 4: Output & Evaluation
        K --> L([Predict Final Probabilities]):::process
        L --> M>"Evaluation Metrics"]:::highlight
    end
