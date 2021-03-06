---
layout: default
title: Contexts
---

# Contexts #

"Contexts" in Liquibase are tags you can add to changeSets to control which will be executed in any particular migration run. Any string can be used for the context name and they are checked case-insensitively.

When you run the migrator though any of the available methods, you can pass in a set of contexts to run. Only changeSets marked with the passed contexts will be run.

If you don't assign a context to a changeSet, it will run all the time, regardless of what contexts you pass in to the migrator.

If you do not specify a context when you run the migrator, ALL contexts will be run.

Here is an example of a change set using the context attribute:
{% highlight xml %}
   <changeSet id="2" author="bob" context="test">
        <insert tableName="news">
            <column name="id" value="1"/>
            <column name="title" value="Liquibase 0.8 Released"/>
        </insert>
        <insert tableName="news">
            <column name="id" value="2"/>
            <column name="title" value="Liquibase 0.9 Released"/>
        </insert>
    </changeSet>
{% endhighlight %}

## Context Syntax ##

Contexts can be specified using AND, OR, ! and parentheses. Without parentheses the order of operations are "!" then "AND" then "OR".

__Examples:__

 * context="!test"
 * context="v1.0 or map"
 * context="v1.0 or map"
 * context="!qa and !master"

 Using a "," to separate contexts works like an OR operation but with the highest precedence.

 __Examples:__

  * "test, qa" is the same as "test OR qa"
  * "test, qa and master" is the same as "(test) OR (qa and master)

__Availability:__

* "," separator available in all versions of Liquibase
* "AND, OR, !, parentheses" added in 3.2.0


## Using Contexts for Test Data ##

If you are managing your test data with Liquibase, the best way to include it is in-line with all your other changeSets, but marked with a "test" context. That way, when you want your test data inserted you can run the migrator with the "test" context. When it comes time to migrate your production database, don't include the "test" context, and your test data not be included. If you have multiple test environments or test data sets, simply tag them with different contexts such as "min-test", "integration-test", etc.

*NOTE: to exclude "test" contexts when updating another database, such as production, you will need to pass at least one context flag. Otherwise it will run ALL contexts, including "test." You can pass a non-existent context flag, such as "prod", which will tell it to run all changes without context as well as any with the "prod" flag (which will probably be zero).*

Using contexts to control test data is better than having a separate changeLog tree because later refactorings and changes will be applied to existing test data the same as they are applied to production data. If you had a set of test data that was created and simply added after the database is set up, you would be constantly manually updating your test data scripts to keep them in line with the current database schema.

## Using Contexts for Multi-DBMS Change Logs ##

You can use contexts to control which change sets run on which databases, but the better option is to use the built-in "dbms" tag on the changeSet tag.
