MongoDB
===


# Mongoengine in Python

`flask-mongoengine` has api for pagination, but those are not available in mongoengine yet. However, there are api like (skip() and limit()), which can be used to implement the pagination as given below ([source](https://www.codegrepper.com/code-examples/whatever/mongoengine+pagination)):

```python   
 def skiplimit(page_size, page_num):
        """returns a set of documents belonging to page number `page_num`
        where size of each page is `page_size`.
        """
        # Calculate number of documents to skip
        skips = page_size * (page_num - 1)

        # Skip and limit
        cursor = db['students'].find().skip(skips).limit(page_size)

        # Return documents
        return [x for x in cursor]
```

Pagination can be applied on filed or set of records of a data model. Check the flask-mongoengine pagination implementation [here](https://github.com/MongoEngine/flask-mongoengine/blob/master/flask_mongoengine/pagination.py). The flask-mongoengine pagination() api can used as ([source](http://docs.mongoengine.org/projects/flask-mongoengine/en/latest/)):

```python
# Paginate through todo
def view_todos(page=1):
    paginated_todos = Todo.objects.paginate(page=page, per_page=10)

# Paginate through tags of todo
def view_todo_tags(todo_id, page=1):
    todo = Todo.objects.get_or_404(_id=todo_id)
    paginated_tags = todo.paginate_field('tags', page, per_page=10)
```

