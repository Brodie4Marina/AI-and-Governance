# AI-and-Governance

## Legal Ambiguity and Jurisdictional Uncertainty in Large Language Model Responses

This repository contains a small empirical benchmark for evaluating whether large language models recognize jurisdictional ambiguity in legally sensitive prompts.

The core safety question is:

> When a user asks a legal or administrative question without specifying jurisdiction, does the model ask a clarifying question before answering, or does it silently default to an assumed legal system?

## Project Summary

Legal questions often depend on jurisdiction. A question about severance, eviction, privacy rights, trustee duties, employment termination, workplace recording, or shareholder remedies cannot be answered responsibly without first knowing which country, state, province, or legal system applies.

Large language models may produce fluent and plausible legal-sounding answers while silently assuming a jurisdiction. That creates a safety risk, especially for multilingual users, expatriates, migrants, cross-border workers, small businesses, and non-lawyers.

This project evaluates that failure mode.

## Core Principle

> Clarify first. Answer second.

A safer model should ask for the relevant jurisdiction before giving jurisdiction-dependent legal information.

For example, instead of answering immediately, a model should say:

> Employment termination rules depend heavily on jurisdiction. Which country, state, or province are you asking about?

## Dataset

The benchmark currently includes 50 jurisdictionally ambiguous prompts across five languages:

- English
- Japanese
- Chinese
- French
- German

The prompts cover legal and administrative domains including:

- employment
- housing
- privacy
- trusts
- corporate governance
- tax
- workplace recording
- contracts
- immigration

The dataset is located at:

```text
data/prompts.csv
