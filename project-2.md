# Project 2

It's time to build a full-stack application leveraging Spring for the application server and HTML, CSS, and JavaScript for UI! The concept and functionality for this application will be up to you and your teammates! Requirements below:

## High-Level Requirements

Application must leverage the full stack:

-   AWS SQL/PostGreSQL for persistence
-   API built with Java 8 and Spring 5
-   UI built with HTML, CSS, and JavaScript

### Technology framework requirements:

-   Java API will leverage the Spring Framework
-   Java API will use Spring Data JPA to communicate with the DB
-   Java API will be RESTful (though HttpSession will be permitted)
-   Java API will be unit tested using JUnit and Mockito, with coverage reports generated using Jacoco
-   Complete CI/CD pipelines will use AWS CodePipeline

### Other requirements:

-   Application will demonstrate at least ten individual user stories
-   Application's own data model must be sufficiently complex (i.e. minimum 3 tables)
-   SQL DB will be deployed to the cloud
-   Java API will be deployed to the cloud (AWS CodePipeline)
-   UI application will be deployed to the cloud (Azure Static Website on S3 Storage)
-   Java API will have >=70% test (line) coverage for service layer with validations (Used EclEmma or JaCoCo plugin to generate these reports)
-   Java API will leverage Spring's MockMvc for integration/e2e tests of controller endpoints
-   At least one external API must be leveraged

# Required Challenge Goals (Select 1):

-   Learn & Implement ReactJS
-   Learn & Implement Spring Security

## Other Thoughts

The project concepts must be approved by the trainer. Remember to keep user stories clear and unambiguous. Keep in mind that you only have 2 weeks to work on this project so make your MVP something attainable. In addition to your project proposal, your teams should be structured with one team leader and a person or persons who fulfill the role of Gitflow manager and DevOps engineer. AVOID dividing the work into API and UI for the team members, everyone should have a hand in ALL aspects of this application.

## Repositories

In order to make your repositories accessible to your AWS Accounts via CodePipeline, it is recommended that you create two repositories under your own personal account. One team member can host the repo for the API and another member can host the repo for the UI. Both must leverage the AWS CI/CD pipeline

## Presentations

Presentations will occur on the afternoon of Friday, September 9th, 2022. All team members must have a speaking role in the presentation of the application, and a **Slide Deck** must accompany your presentation. Aim for 20-25min.
