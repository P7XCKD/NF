<p align="center">

<a href="https://ibb.co/0y4jv78d"><img src="https://i.ibb.co/8gvDtCTS/image.png" alt="image" border="0"></a>

<p>
    <span style="float:left;">
        <h3>DBMS Experiment 1
    </span>
    <span style="float:right; text-align:right;"> 
        Name: Dev Rakesh Mandora<br>
        Roll Number: B-62 <br>
        Batch: SB4</h3>
    </span>
</p>

<br clear="both">

### Aim

To identify a real-world problem related to Climate Intelligence for Heatwave and develop a suitable problem statement. To design an Entity-Relationship (ER) Model representing the entities, attributes, and relationships involved in a heatwave monitoring and prediction system.

### Objectives

- To understand the concept of an Entity-Relationship (ER) Diagram.
- To identify the major entities involved in a Climate Intelligence for Heatwave system.
- To identify and define the attributes of each entity.
- To identify the relationships between different entities.
- To represent the cardinality between entities using 1:1 and 1:M relationships.
- To understand how climate data and observations are used for heatwave prediction.
- To represent the generation of heatwave forecasts and risk alerts.
- To develop a conceptual database model before implementing the actual database.

### Software Required

- [draw.io](https://app.diagrams.net/) / [Mermaid Live Editor](https://mermaid.live/edit#pako:eNpVjUFPg0AQhf_KZk6a0AYWkLoHEwvaSxM99CT0sIGBJS27ZFlSK_DfXWiM-k4z8773ZoBcFQgMyrO65IJrQw5JJonVcxoLXXem4d2RrFZP4w4NaZTE60i2dztFOqHatpbV_Y3fzhCJh_2MITGilqfpZsVL_k3iSJJ0z1uj2uNf53BRI3lJ63dh6_87QqNNvaYlZyVf5VyTmOsFAQcqXRfAjO7RgQZ1w-cVhtnNwAhsMANmx4LrUwaZnGym5fJDqeYnplVfCbDd585ufVtwg0nNK81_EZQF6lj10gDz_KUC2ACfwHwvWLs-9Tae79OIeqEDV3sN1h4NHjc0oK4fhiGdHPhafrrrTRS6VvTBjSKXhtM3qEN1BA)


### Theory

### i) Problem Statement

The Climate Intelligence for Heatwave system is designed to monitor climate conditions, collect weather observations, analyze climate data, predict heatwave conditions, and generate risk alerts.

The system stores information about different locations, their climate data, users, monitoring systems, observations, prediction models, heatwave forecasts, and risk alerts.

The collected climate data such as temperature, humidity, wind speed, and other parameters is analyzed using prediction models. Based on this analysis, the system generates heatwave forecasts and triggers appropriate risk alerts.

### ER Diagram

## i) Entities & Attributes

| Entity | Type | Attributes |
|---|---|---|
| **User** | Strong Entity | `user-id`<br>`age`<br>`name` |
| **City** | Strong Entity | `city-code`<br>`city-name`<br>`population` |
| **Weather Station** | Strong Entity | `station-id`<br>`coordinates` |
| **Sensor** | Strong Entity | `sensor-id`<br>`sensor-type` |
| **Weather Data** | Weak Entity | `temperature`<br>`humidity`<br>`heat-index` |
| **Heatwave Predictor** | Strong Entity | `prediction-id`<br>`prediction-time`<br>`prediction-date` |
| **Alert System** | Strong Entity | `alert-id`<br>`alert-level`<br>`alert-msg` |
| **Manager** | Strong Entity | — |

## ii) Entities & Relationships

| Entity | Relationship | Entity | Cardinality |
|---|---|---|---|
| **User** | `belongs to` | **City** | `M : 1` |
| **City** | `contains` | **Weather Station** | `1 : M` |
| **Manager** | `manages` | **Weather Station** | `1 : M` |
| **Weather Station** | `operates` | **Sensor** | `1 : M` |
| **Sensor** | `collects` | **Weather Data** | `1 : M` |
| **Weather Data** | `feeds` | **Heatwave Predictor** | `M : 1` |
| **Heatwave Predictor** | `triggers` | **Alert System** | `1 : M` |


> ![ER Diagram](https://github.com/P7XCKD/NF/raw/main/Notes%20Factory/sem%203/DBMS/soft/.attachments/afa29e5ebbbea7523c5f791ba453f9bd44e0f0c4.png)

### Outcome

Successfully designed a conceptual ER model for the Climate Intelligence for Heatwave system, representing its major entities, attributes, relationships, and cardinalities.

The model provides a clear structural representation of how climate data is collected, monitored, analyzed, used for heatwave prediction, and converted into risk alerts.

### Conclusion

With the help of the ER diagram for Climate Intelligence for Heatwave, I understood how to identify entities, attributes, relationships, and cardinalities for a real-world application. The diagram provides a clear conceptual structure for managing climate data, observations, prediction models, heatwave forecasts, and risk alerts, which can be used as a foundation for designing the actual database.