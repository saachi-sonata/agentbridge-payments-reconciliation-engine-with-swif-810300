# Architecture Documentation

## Overview
This RAG implements Payments Reconciliation Engine with SWIFT Gateway for Banking & Finance use cases.

## Components
1. **Customer Intake**: Collect, validate and normalize positions from SWIFT Gateway; attach a runId and timestamp for traceability.
2. **Retrieve**: Execute retrieve phase for the RAG pattern: persist interim state, enforce guardrails, and emit structured JSON results.
3. **Ground**: Execute ground phase for the RAG pattern: persist interim state, enforce guardrails, and emit structured JSON results.
4. **Sanctions Screening**: Sanctions Screening across joined datasets; branch on thresholds using decision gates; write metrics (success/error counts) for observability.
5. **Limit Control**: Limit Control across joined datasets; branch on thresholds using decision gates; write metrics (success/error counts) for observability.
6. **Underwriting**: Underwriting across joined datasets; branch on thresholds using decision gates; write metrics (success/error counts) for observability.
7. **Risk Scoring**: Risk Scoring across joined datasets; branch on thresholds using decision gates; write metrics (success/error counts) for observability.
8. **Reconciliation Summary**: Assemble final payload with status, artifacts, KPIs and audit trail; store to Case Management; return response JSON for the client.

## Data Flow
- Input: Customer Intake
- Processing: 8 sequential steps
- Output: Reconciliation Summary
