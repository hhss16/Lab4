# Instructions to run this project

Please make sure you have pip and pipenv installed first. 

```sh
git clone https://github.com/hhss16/Lab4
cd Lab4
pipenv shell
pipenv install 
python manage.py makemigrations 
python manage.py migrate
python manage.py runserver
```

## Previews & Information

Then access `http://127.0.0.1:8000/api/menu-items` or `http://127.0.0.1:8000/api/categories` - full support for **GET** and **POST** for *menu items* and full support for **GET**, and **POST** for *categories*. 

![Preview Lab 4](https://res.cloudinary.com/dpebhamdp/image/upload/v1667830608/Labs/Lab%204/categories_fkzqmm.png)

![Preview Lab 4](https://res.cloudinary.com/dpebhamdp/image/upload/v1667830608/Labs/Lab%204/menu-items_jaua4i.png)


For filtering, searching and pagination, only these three lines added in the views.py file 

```python
    ordering_fields = ['price', 'inventory']
    filterset_fields = ['price', 'inventory']
    search_fields = ['category__title']
```

![searching](https://res.cloudinary.com/dpebhamdp/image/upload/v1667830607/Labs/Lab%204/search_seecz8.png)

![pagination](https://res.cloudinary.com/dpebhamdp/image/upload/v1667830607/Labs/Lab%204/pagination_srxean.png)

![filter + search + pagination](https://res.cloudinary.com/dpebhamdp/image/upload/v1667830608/Labs/Lab%204/search_filter_pagination_hnhgrh.png)


Only these eight lines in the **settings.py** file for filtering, searching and pagination. Learners are already familiar. 

```python
REST_FRAMEWORK = {
    'DEFAULT_FILTER_BACKENDS': [
        'rest_framework.filters.OrderingFilter',
        'rest_framework.filters.SearchFilter',
    ],
    'DEFAULT_PAGINATION_CLASS': 'rest_framework.pagination.PageNumberPagination',
    'PAGE_SIZE': 2
}
```

## Valid URLS
* http://127.0.0.1:8000/api/menu-items 
* http://127.0.0.1:8000/api/menu-items?page=1
* http://127.0.0.1:8000/api/menu-items?ordering=price
* http://127.0.0.1:8000/api/menu-items?ordering=-price
* http://127.0.0.1:8000/api/menu-items?ordering=price,inventory
* http://127.0.0.1:8000/api/menu-items?ordering=inventory
* http://127.0.0.1:8000/api/menu-items?ordering=-inventory
* http://127.0.0.1:8000/api/menu-items?search=Main

* http://127.0.0.1:8000/api/categories
* http://127.0.0.1:8000/api/categories?page=1 
