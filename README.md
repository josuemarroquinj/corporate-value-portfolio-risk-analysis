# Corporate Value Creation & Portfolio Risk Analysis (EVA-VaR Model)

[![Python 3.10+](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Framework: Pandas/SciPy](https://img.shields.io/badge/Framework-Pandas%20%7C%20SciPy-orange.svg)](https://scipy.org/)

## 📌 Resumen del Proyecto

Este proyecto integra herramientas de **Finanzas Corporativas Avanzadas** (Economic Value Added - EVA, WACC y Ecuación de Hamada para desapalancamiento de Beta) con **Teoría Cuantitativa de Portafolios y Gestión de Riesgo de Mercado** (Value at Risk - VaR Paramétrico y Monte Carlo).

El objetivo principal es resolver un modelo de optimización cuadrática que maximice la creación de valor económico sujeto a límites de riesgo de cola para una muestra representativa de activos de alta capitalización (`NVDA`, `MSFT`, `AMZN`, `BRK.B`, `XOM`).

---

## 📐 Marco Teórico y Formulación Matemática

### 1. Creación de Valor Económico (EVA & ROIC Spread)
El EVA mide el valor financiero generado por la firma por encima del costo de oportunidad del capital invertido:

$$\text{NOPAT} = \text{EBIT} \times (1 - t_{\text{efectiva}})$$

$$\text{EVA} = \text{NOPAT} - (\text{Capital Invertido} \times \text{WACC})$$

$$\text{EVA Spread} = \text{ROIC} - \text{WACC} \quad \text{donde} \quad \text{ROIC} = \frac{\text{NOPAT}}{\text{Capital Invertido}}$$

### 2. Modelo CAPM y Ajuste de Estructura Financiera (Hamada)
El costo de capital propio ($K_e$) se determina mediante el modelo CAPM, mientras que la tasa de desapalancamiento del riesgo sistemático para estimar la Beta de negocio ($\beta_U$) utiliza la Ecuación de Hamada:

$$K_e = R_f + \beta_L \cdot (\text{ERP})$$

$$\beta_U = \frac{\beta_L}{1 + (1 - t_{\text{efectiva}}) \cdot \left(\frac{D}{E}\right)}$$

### 3. Función Objetivo de Optimización (Fase 3)
Maximización de retorno ajustado por EVA ajustado por la covarianza del mercado:

$$\max_{w} \quad w^T \mathbf{S}_{\text{EVA}} - \lambda \left( w^T \mathbf{\Sigma} w \right)$$

$$\text{Sujeto a:} \quad \sum_{i=1}^{n} w_i = 1, \quad 0 \le w_i \le 0.40, \quad \text{VaR}_{95\%}(w) \le \text{VaR}_{\text{máximo}}$$

---

## 📂 Estructura del Repositorio

```text
corporate-value-portfolio-risk-analysis/
├── .gitignore                                  # Exclusión de archivos temporales
├── README.md                                   # Documentación principal del proyecto
├── requirements.txt                            # Dependencias y librerías de Python
├── data/
│   ├── raw/
│   │   └── Financials2.xlsx                    # Estados financieros originales
│   └── processed/
│       ├── fundamental_eva_metrics.csv         # Métricas calculadas en Fase 1
│       └── market_data_returns.csv             # Retornos diarios y volatilidad (Fase 2)
└── notebooks/
    ├── 00_fundamental_financial_processing.ipynb  # FASE 1: EVA, WACC, Hamada & ROIC
    ├── 01_market_data_collection.ipynb             # FASE 2: Precios, Betas & VaR
    └── 02_portfolio_eva_var_optimization.ipynb     # FASE 3: Optimización Cuadrática EVA-VaR

# Corporate Value, Portfolio Risk and Market Performance

## Doctoral Research Project in Corporate Finance

This repository contains the computational and empirical framework for an applied research project examining the relationship between corporate value creation, financial market performance, systematic risk, portfolio diversification, and Value-at-Risk (VaR).

## Research Question

To what extent is economic value creation, measured through Economic Value Added (EVA), associated with stock market performance, systematic risk, portfolio contribution, and Value-at-Risk among selected U.S. corporations?

## Companies

- Amazon (AMZN)
- Nvidia (NVDA)
- Microsoft (MSFT)
- Exxon Mobil (XOM)
- Berkshire Hathaway Class B (BRK-B)

## Main Research Components

1. Economic Value Added (EVA)
2. Stock returns
3. Systematic risk and Beta
4. CAPM
5. Portfolio theory
6. Value-at-Risk (VaR)
7. EVA-market integration

## Research Period

January 1, 2022 – December 31, 2025

## Project Status

Version 0.1 — Research infrastructure and project setup.
