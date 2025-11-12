# convert-legacy Workflow Rule

This rule defines the convert-legacy workflow.

## Workflow Description

Converts legacy BMAD v4 or similar items (agents, workflows, modules) to BMad Core compliant format with proper structure and conventions

## Workflow Definition

# Convert Legacy - BMAD v4 to v6 Converter Configuration
name: "convert-legacy"
description: "Converts legacy BMAD v4 or similar items (agents, workflows, modules) to BMad Core compliant format with proper structure and conventions"
author: "BMad"

# Critical variables load from config_source
config_source: "{project-root}/.osx/bmb/config.yaml"
output_folder: "{config_source}:output_folder"
user_name: "{config_source}:user_name"
communication_language: "{config_source}:communication_language"
date: system-generated

# Optional docs that can be provided as input
recommended_inputs:
  - legacy_file: "Path to v4 agent, workflow, or module to convert"

# Module path and component files
installed_path: "{project-root}/.osx/bmb/workflows/convert-legacy"
template: false # This is an action/meta workflow - no template needed
instructions: "{installed_path}/instructions.md"
validation: "{installed_path}/checklist.md"

# Output configuration - Creates converted items in appropriate module locations
default_output_folder: "{project-root}/.osx/{{target_module}}/{{item_type}}/{{item_name}}"

# Sub-workflows that may be invoked for conversion
sub_workflows:
  - create_agent: "{project-root}/.osx/bmb/workflows/create-agent/workflow.yaml"
  - create_workflow: "{project-root}/.osx/bmb/workflows/create-workflow/workflow.yaml"
  - create_module: "{project-root}/.osx/bmb/workflows/create-module/workflow.yaml"

standalone: true


## Usage

Reference this workflow with `@workflow-convert-legacy` to execute the guided workflow.

## Module

Part of the BMAD BMB module.
