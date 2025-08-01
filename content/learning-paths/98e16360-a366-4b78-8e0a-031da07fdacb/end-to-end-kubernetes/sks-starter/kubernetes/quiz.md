---
title: "Knowledge Check"
id: "quiz-kubernetes"
passing_percentage: 75
questions:
    - id: "q1"
      text: "A Deployment consists of:"
      type: "mcq"
      marks: 2
      options:
        - id: "a"
          text: "One or more Containers"
        - id: "b"
          text: "One or more Pods"
          is_correct: true
    
    - id: "q2"
      text: "What is a Pod?"
      type: "mcq"
      marks: 2
      options:
        - id: "a"
          text: "A host machine or node where containers are deployed that have shared IP addresses"
        - id: "b"
          text: "A Kubernetes Master, responsible for scheduling and coordinating application containers"
        - id: "c"
          text: "A group of one or more containers that have shared IP addresses"
          is_correct: true
        - id: "d"
          text: "A single container with a single IP address"
        - id: "e"
          text: "A single container with a shared IP address"


    - id: "q3"
      text: "What are Nodes?"
      type: "mcq"
      marks: 2
      options:
        - id: "a"
          text: "Nodes are managed and coordinate the cluster"
        - id: "b"
          text: "Nodes are worker machines in Kubernetes and used to run Pods"
          is_correct: true
        - id: "c"
          text: "Nodes are a group of one or more Pods"

    - id: "q4"
      text: "The command > kubectl describe pod lists:"
      type: "mcq"
      multiple_answers: true
      marks: 2
      options:
        - id: "a"
          text: "Name of the Pod"
          is_correct: true
        - id: "b"
          text: "Containers of the Pod"
          is_correct: true
        - id: "c"
          text: "IP of the Pod"
          is_correct: true
        - id: "d"
          text: "Logs of the Pod"
        - id: "e"
          text: "Events of the Pod"   
          is_correct: true
layout: "quiz"
type: "quiz"
---
