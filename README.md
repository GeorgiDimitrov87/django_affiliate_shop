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
The second option is to use django-cms apphooks. Shopit comes with a couple of those for different application parts. ShopitApphook is the main one, and one that should always be attached to a page (if the urls are not already added). Then there are other optional apphooks for account, categorization & products. If you want to keep it simple, and not have to set every application part individually. You can add to your settings:

SHOPIT_SINGLE_APPHOOK = True
This will load all the neccesary urls under the ShopitApphook.
