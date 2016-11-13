# 2. Normalization

**(14 points total)** 


Some warmup questions:

1. (2 points) **Q2.1**: You have a relation `R(A,B,C)` and functional dependencies 
  `A->C, C->B`

  * What are all the non-trivial functional dependencies in the closure
    that have  only one attribute on the right side? The definition of trivial is a functional dependency where the right hand side is included in the left hand side. These are the functional dependencies that are true via reflexivity.
  * What are all the minimal keys of `R`? (We do not care about super keys)

2. (3 points) **Q2.2**: You have a relation `S(A, B, C, D)` and functional dependencies 
  `AB->D, BD->C, CD->A, and AD->B`

  * What are all the non-trivial functional dependencies in the closure
    that have  only one attribute on the right side?
  * What are all the minimal keys of `S`? (We do not care about super keys)

Now for a real application. 
The Iowa dataset has the following un-normalized schema:

    CREATE TABLE iowa (
        date date,
        convenience_store character varying(128),
        store integer,
        name character varying(128),
        address character varying(128),
        city character varying(128),
        zipcode text,
        store_location character varying(128),
        county_number integer,
        county character varying(128),
        category integer,
        category_name character varying(128),
        vendor_no integer,
        vendor character varying(128),
        item text,
        description character varying(128),
        pack integer,
        liter_size integer,
        state_btl_cost double precision,
        btl_price double precision,
        bottle_qty integer,
        total double precision
    );

Suppose we have the functional dependencies:

    store → convenience_store, address, name, city, zipcode, store_location,
             county_number, county
    vendor_no → vendor
    category → category_name
    item → category, liter_size, description, state_btl_cost btl_price
    date, store, vendor_no, item → pack, bottle_qty, total


3. (2 points) **Q2.3**: What are the keys in 'iowa'?

4. (3 points) **Q2.4**: Decompose `iowa` into 3NF (Third Normal Form).  Write a few sentences to justify why you chose the tables you did.  

5. (2 points) **Q2.5**: Is your schema redundancy and anomaly free?  Justify your answer in
a few sentences.

6. (2 points) **Q2.6**: We want to ensure that an order cannot have a individual bottle price more than
50.00 (`btl_price`).  Can you enforce this using functional dependencies?  Justify your answer

7. (1 point) **Q2.7**: Let's verify whether `item` indeed determines the `vendor` name. How many distinct `vendor` values exist for `item` number `3326` in the `iowa` dataset?  Solve this by running a SQL query.

8. (1 point) **Q2.8**: In class, we discussed that functional dependencies (and constraints in general) cannot be determined just by looking at data in the database. Argue in one or two sentences whether or not `item -> vendor` should actually be a functional dependency and why given the design of the database.  

# X.  For Giggles (Optional)

**(0 points total)**

If you are still interested in this dataset, it turns out that you _can_ normalize the store data!
The state of iowa has released a dataset of all liquor stores as a dataset available at
https://data.iowa.gov/Economy/Iowa-Liquor-Stores/ykb6-ywnd

This dataset provides us information about store attributes so we could factor those out of the iowa dataset.


# Submission for Normalization

**Please submit this section of HW3 through the following Google form**

https://goo.gl/forms/lYikjAvzyLXmXcmg2
