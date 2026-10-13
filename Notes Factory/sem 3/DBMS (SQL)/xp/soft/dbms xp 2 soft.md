> [!abstract] EER DIAGRAM NEED CORRECTION CITRY CODE IS TOUCHING COORDINATES ARROW
> 
> Contents

 <p align="center">

<a href="https://ibb.co/0y4jv78d"><img src="https://i.ibb.co/8gvDtCTS/image.png" alt="image" border="0"></a>

<p>
    <span style="float:left;">
        <h3>DBMS Experiment 2
    </span>
    <span style="float:right; text-align:right;"> 
        Name: Dev Rakesh Mandora<br>
        Roll Number: B-62 <br>
        Batch: SB4</h3>
    </span>
</p>

<br clear="both">

### Aim:
To map the ER/EER model to Relational Schema Model.

### Objective:
To convert the given ER/EER model into a Relational Schema Model using appropriate ER-to-Relational mapping techniques.

### Software Required:
- Draw.io

### Theory:

ER/EER models are converted into relational schemas by mapping entities, attributes, relationships, and specialization/generalization into relational tables.

**1. Strong Entity Mapping:**  
Each strong entity is converted into a separate relation. The key attribute of the entity is used as the Primary Key (PK).

**2. Weak Entity Mapping:**  
A weak entity is mapped to a separate relation using the key of its owner entity along with its partial key. This mapping is not required in the given ER/EER model as no weak entity is present.

**3. 1:1 Mapping:**  
For a one-to-one relationship, the primary key of one participating entity can be placed as a foreign key in the other relation. No 1:1 relationship is present in the given model.

**4. 1:N Mapping:**  
For a one-to-many relationship, the primary key of the entity on the 1-side is added as a foreign key to the relation on the N-side.

**5. M:N Mapping:**  
For a many-to-many relationship, a separate relation is created containing the keys of the participating entities. No M:N relationship is present in the given model.

**6. Multivalued Attribute Mapping:**  
A multivalued attribute is represented using a separate relation. No multivalued attribute is present in the given model.

**7. N-ary Relationship Mapping:**  
An N-ary relationship involving more than two entities is represented using a separate relation. No N-ary relationship is present in the given model.

**8. Generalization / Specialization Mapping:**  
For generalization/specialization, the superclass and its subclasses are represented using separate relations. The key of the superclass is used in the subclass relations.

### Output:
> [!summary] Climate Intelligence for Heatwave
> ![image](.attachments/cdf1fe0b2758c77dbdbc556af4e50aad86a78a23.png) 

The following mapping steps were used to create the Relational Schema Model:

1. **Strong Entity Mapping:**  
   Converted the strong entities `User`, `City`, `Weather Station`, `Sensor`, `Weather Data`, `Heatwave Predictor`, and `Alert System` into separate relations.

2. **1:N Mapping:**  
   Mapped the 1:N relationships by adding the primary key of the 1-side as a foreign key in the N-side relations.

3. **Generalization / Specialization Mapping:**  
   Mapped the `User` specialization into `normal_user` and `manager` relations using `user_id` from the `User` relation.

4. Added the appropriate **Primary Key (PK)** and **Foreign Key (FK)** connections between the relations and represented the final Relational Schema Model in Draw.io.

### Outcome:
Successfully converted the given ER/EER model into a Relational Schema Model using Strong Entity Mapping, 1:N Mapping, and Generalization / Specialization Mapping.

### Conclusion:
The experiment successfully demonstrated the conversion of an ER/EER model into a relational schema by identifying entities, mapping 1:N relationships using foreign keys, and representing the generalization/specialization hierarchy using separate relations.