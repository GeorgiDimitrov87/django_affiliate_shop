Install using pip:

pip install django-shopit

You should follow django-cms & django-shop installation guide first, and then add the following to your settings:

INSTALLED_APPS = [
    ...
    'adminsortable2',
    'mptt',
    'parler',
    'shopit',
]

SHOP_APP_LABEL = 'shopit'
SHOP_PRODUCT_SUMMARY_SERIALIZER = 'shopit.serializers.ProductSummarySerializer'
SHOP_CART_MODIFIERS = (
    'shop.modifiers.DefaultCartModifier',
    'shopit.modifiers.ShopitCartModifier',
    ...
)

Urls
There are two ways to configure the urls. First would be to add to your urls.py:

urlpatterns = [
    url(r'^shop/', include('shopit.urls')),
    ...
]
