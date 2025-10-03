# Condensate: FuzDrop-like Protein Phase Separation Predictor

A class project for building a web-based tool to predict liquid-liquid phase separation (LLPS) propensity in proteins, similar to FuzDrop.

## 🎯 Project Overview

This project aims to create a simplified version of FuzDrop - a tool that predicts protein droplet formation propensity. The goal is to build a complete pipeline: **input → features → prediction → visual output**.

## 📋 Table of Contents

- [What is FuzDrop?](#what-is-fuzdrop)
- [System Architecture](#system-architecture)
- [Project Roadmap](#project-roadmap)
- [Technology Stack](#technology-stack)
- [Challenges & Considerations](#challenges--considerations)
- [Getting Started](#getting-started)

## 🧬 What is FuzDrop?

FuzDrop is a computational tool that takes a protein sequence (or UniProt ID) and predicts the propensity for liquid–liquid phase separation (LLPS) / "droplet" formation.

### Key Features:
- **Sequence Input**: Accepts FASTA format or UniProt accession numbers
- **Feature Computation**: Analyzes local composition biases, hydrophobicity, and disorder metrics
- **Predictive Modeling**: Uses statistical/ML models to map features to droplet formation probability
- **Region-level Scoring**: Provides sliding window analysis rather than single sequence scores
- **Visualization**: Generates plots over sequence positions with color coding
- **Web Interface**: User-friendly web frontend for sequence submission and result viewing

### Prediction Types:
- Droplet-promoting regions
- Aggregation-promoting regions within droplets
- Overall phase separation propensity scores

## 🏗️ System Architecture

### Core Components

| Component | Purpose | Implementation Notes |
|-----------|---------|---------------------|
| **Input Parser** | Accept and validate user input (FASTA, raw sequence, UniProt ID) | Start with FASTA/raw sequence for simplicity |
| **Feature Engine** | Compute sequence-derived features (AA frequencies, hydrophobicity, disorder metrics) | Use Biopython and existing libraries |
| **ML Predictor** | Apply trained model to generate predictions | Start with logistic regression, expand to RF/NN |
| **Sliding Window** | Compute per-residue or per-window scores for hotspot identification | Essential for visualization |
| **Visualization** | Generate plots and color-coded regions | Use matplotlib/Plotly |
| **Web Interface** | Frontend for input and backend API for processing | Flask/Django + HTML/JS |
| **Structure Mapping** | Optional 3D visualization with AlphaFold models | Use Mol*/NGL viewers |
| **Deployment** | Host web application with proper resource management | Heroku/AWS/University servers |

### Data Pipeline
Protein Sequence → Feature Extraction → ML Model → Scoring → Visualization → Web Display
## 🗺️ Project Roadmap

### Phase 0: Planning & Scoping
- [ ] Define tool completeness (protein-level vs region-level scoring)
- [ ] Select feature computation methods
- [ ] Identify training datasets (positive/negative examples)
- [ ] Set up development environment

### Phase 1: Core Prototype (Command-line)
- [ ] Implement sequence input and validation
- [ ] Build feature computation pipeline
- [ ] Create dummy/baseline model
- [ ] Test end-to-end pipeline
- [ ] Train initial logistic regression model
- [ ] Evaluate model performance

### Phase 2: Region-level Analysis
- [ ] Implement sliding window feature computation
- [ ] Generate per-window/per-residue scores
- [ ] Create basic plotting functionality
- [ ] Validate region-level predictions

### Phase 3: Visualization & Reporting
- [ ] Design comprehensive plotting system
- [ ] Implement color coding and thresholding
- [ ] Add structure mapping capabilities (optional)
- [ ] Create documentation and tutorials

### Phase 4: Web Development
- [ ] Build web form for sequence input
- [ ] Develop backend API endpoints
- [ ] Implement result visualization in browser
- [ ] Add batch upload functionality (optional)

### Phase 5: Deployment & Production
- [ ] Deploy to hosting platform
- [ ] Implement input validation and error handling
- [ ] Optimize performance (caching, async jobs)
- [ ] Add user authentication and job queuing (optional)

## 🛠️ Technology Stack

### Core Development
- **Language**: Python 3.8+
- **Sequence Processing**: Biopython
- **Numerical Computing**: NumPy, SciPy
- **Machine Learning**: scikit-learn
- **Visualization**: matplotlib, seaborn, Plotly

### Web Development
- **Backend Framework**: Flask (lightweight) or Django (full-featured)
- **API**: Flask-RESTful
- **Frontend**: HTML5, CSS3, JavaScript
- **Interactive Plots**: Plotly.js
- **Structure Viewer**: NGL Viewer or Mol* (optional)

### Data & Storage
- **Database**: SQLite (development), PostgreSQL (production)
- **Caching**: Redis (optional)
- **File Storage**: Local filesystem or cloud storage

### Deployment & DevOps
- **Containerization**: Docker
- **Hosting**: Heroku, AWS, Google Cloud, or University servers
- **Version Control**: Git + GitHub
- **CI/CD**: GitHub Actions (optional)

### Data Sources
- **Training Data**: Published LLPS protein datasets
- **Protein Database**: UniProt
- **Structure Data**: AlphaFold Database (optional)
- **Reference Tools**: FuzDrop datasets for comparison

## ⚠️ Challenges & Considerations

### Technical Challenges
- **Data Quality**: LLPS datasets are limited and potentially biased
- **Feature Engineering**: Critical for model performance - focus on meaningful features
- **Performance**: Large protein sequences may require optimization for sliding window analysis
- **Validation**: Requires rigorous cross-validation and held-out test sets

### User Experience
- **Visualization**: Clear presentation of per-residue scores is non-trivial
- **Interpretability**: Users need explanations for why regions are predicted as high-risk
- **Interface Design**: Balance simplicity with functionality

### Development Considerations
- **Security**: Input sanitization, preventing code injection
- **Robustness**: Error handling for malformed inputs and server issues
- **Scalability**: Resource management for concurrent users
- **Structure Integration**: AlphaFold model parsing and sequence mapping complexity

## 🚀 Getting Started

### Prerequisites
```bash
# Python 3.8+
python --version

# Required packages (install via pip)
pip install biopython numpy scipy scikit-learn matplotlib plotly flask
```

### Quick Start
1. Clone this repository
2. Set up virtual environment
3. Install dependencies
4. Run initial prototype scripts
5. Launch web development server

### Development Setup
```bash
# Create virtual environment
python -m venv condensate-env
source condensate-env/bin/activate  # On Windows: condensate-env\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Run tests
python -m pytest tests/

# Start development server
flask run --debug
```

---FINISH

