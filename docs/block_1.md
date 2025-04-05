
This part of the Data Store Days consists of a slide presentation: Download here (TODO: add link for slides)

We also refer to the [Data Store Wiki](https://datastore.bam.de/en/home) for all the definitions of the main concepts in openBIS and in the Data Store project.

## BAM Data Model and Masterdata definitions

OpenBIS and the data therein is organized following a folder-like structure space/project/collection/object_types/dataset_types. The object types and dataset types are the main data structures used in openBIS and they represent tangible and intangible entities and their attached metainformation. The data model in openBIS is defined by the object types and its assigned properties, plus the parent-child relationships created between the objects. The assigned properties have different datatypes: strings, floats,..., and they can be controlled vocabularies. A controlled vocabulary is an enumeration of strings that the assigned property can take. We call Masterdata (or schema) to all the defined object types, property types, and vocabularies without the actual data populating the assigned properties and without the parent-child relationships. These parent-child relationships allows to connect object types hence representing the full workflow done during the scientific activity.

For example, `Instrument` and `Sample` are object types with a set of assigned properties like `name`, `manufacturer`, `device_model_name`, or `physical_state`. `physical_state` is a controlled vocabulary and can only be defined as `"solid"`, `"liquid"`, and `"gaseous"`. Both object types can be connected via a parent-child relationship, representing perhaps a characterization measurement of an instrument over a synthesized sample.

<div class="click-zoom">
    <label>
        <input type="checkbox">
        <img src="../assets/example-workflow-objects.drawio.svg" alt="Example of an object type and its assigned properties and the workflow which can be constructed in openBIS." width="80%" title="Click to zoom in">
    </label>
</div>

In openBIS, we also distinguish between the ELN and the Inventory in order to differentiate between objects which exists in a laboratory and can be reused by different team members from the actual objects used during the scientific workflow.

## Represent your research workflow in the Data Store

In order to represent your workflow in the Data Store, you need to:
- Identify the tangible and intangible object types you need.
- Explore the currently defined object types and their assigned properties to check if any of them align with the object types that you need.
- For those cases where you do not find an object type already defined, extend the current Masterdata (see [Block II - BAM Masterdata](block_2.md)).
- Once the Masterdata contains all the object types that you need, populate your schema with the actual data (see [Block III - Representing workflows in the BAM Data Store](block_3.md)).

In this block, we will focus on the initial two points. For this example, we will assume that all the object types we need are already defined in the current BAM Masterdata and that we do not need to extend it.


### Identify your object types

You can either use a piece of paper or the drawio document (TODO: add link) that we prepared from the Data Store team.

We are going to construct a directed acyclic graph (DAG) representing the workflow in your research. As an example, let's consider we have:

<div class="click-zoom">
    <label>
        <input type="checkbox">
        <img src="../assets/example-xrd-workflow.drawio.svg" alt="Example of an XRD characterization workflow." width="80%" title="Click to zoom in">
    </label>
</div>

We also identified some of the objects with the Inventory and some with the ELN. Furthermore, we could identify them with already existing Masterdata and assign the corresponding properties to each object.

<div class="click-zoom">
    <label>
        <input type="checkbox">
        <img src="../assets/example-xrd-workflow-generic.drawio.svg" alt="Example of an XRD characterization workflow with generic BAM Masterdata." width="80%" title="Click to zoom in">
    </label>
</div>


The difference between both workflows is that the second one uses object types already defined in BAM Masterdata: `Chemical`, `Instrument`, `Experimental Step`, and `Sample`. Visit [bam-masterdata](https://github.com/BAMresearch/bam-masterdata) in Github to explore the current Masterdata.

??? note "Real case scenario"
    This example is actually too simplistic. In reality, the chances that the current BAM Masterdata does not have the object types properly defined as you need are high. This situation also depends about how fine-grained you want to defined your workflow, and the requirements of your project. A good scientific practice is to represent your workflows as minimal as possible while keeping reproducibility maximize.