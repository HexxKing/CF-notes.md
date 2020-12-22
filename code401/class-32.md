# [Django REST Framework Permissions](https://www.django-rest-framework.org/api-guide/permissions/)
- Permissions are used to grant or deny access for different classes of users to different parts of the API.
- Permissions in REST framework are always defined as a list of permission classes.
  - Before running the main body of the view each permission in the list is checked. If any permission check fails an `exceptions.PermissionDenied` or `exceptions.NotAuthenticated` exception will be raised, and the main body of the view will not run.
- Object level permissions are used to determine if a user should be allowed to act on a particular object, which will typically be a model instance.
  - If you're writing your own views and want to enforce object level permissions, or if you override the get_object method on a generic view, then you'll need to explicitly call the .check_object_permissions(request, obj) method on the view at the point at which you've retrieved the object.
```
    def get_object(self):
      obj = get_object_or_404(self.get_queryset(),` `pk=self.kwargs["pk"])
      self.check_object_permissions(self.request, obj)
      return obj
```
  - For performance reasons the generic views will not automatically apply object level permissions to each instance in a queryset when returning a list of objects.
  - Often when you're using object level permissions you'll also want to filter the queryset appropriately, to ensure that users only have visibility onto instances that they are permitted to view.
- The default permission policy may be set globally, using the DEFAULT_PERMISSION_CLASSES setting
```
REST_FRAMEWORK = {
    'DEFAULT_PERMISSION_CLASSES': [
        'rest_framework.permissions.IsAuthenticated',
    ]
}
```
- You can also set the authentication policy on a per-view, or per-viewset basis, using the APIView class-based views.
```
from rest_framework.permissions import IsAuthenticated
from rest_framework.response import Response
from rest_framework.views import APIView

class ExampleView(APIView):
    permission_classes = [IsAuthenticated]

    def get(self, request, format=None):
        content = {
            'status': 'request was permitted'
        }
        return Response(content)
```
- The `AllowAny` permission class will allow unrestricted access, regardless of if the request was authenticated or unauthenticated
- The `IsAuthenticated` permission class will deny permission to any unauthenticated user, and allow permission otherwise. This permission is suitable if you want your API to only be accessible to registered users.
- The `IsAdminUser` permission class will deny permission to any user, unless `user.is_staff` is True in which case permission will be allowed.This permission is suitable if you want your API to only be accessible to a subset of trusted administrators.
- The `IsAuthenticatedOrReadOnly` will allow authenticated users to perform any request. Requests for unauthorised users will only be permitted if the request method is one of the "safe" methods; `GET`, `HEAD` or `OPTIONS`. This permission is suitable if you want to your API to allow read permissions to anonymous users, and only allow write permissions to authenticated users.
- The `DjangoModelPermissions` class ties into Django's standard django.contrib.auth model permissions. This permission must only be applied to views that have a `.queryset` property set. Authorization will only be granted if the user is authenticated and has the relevant model permissions assigned.
  - `POST` requests require the user to have the add permission on the model.
  - `PUT` and `PATCH` requests require the user to have the change permission on the model.
  - `DELETE` requests require the user to have the delete permission on the model.
  - The default behaviour can also be overridden to support custom model permissions. For example, you might want to include a view model permission for `GET` requests.
  - To use custom model permissions, override `DjangoModelPermissions` and set the `.perms_map` property. Refer to the source code for details
- `DjangoModelPermissionsOrAnonReadOnly` is similar to `DjangoModelPermissions`, but also allows unauthenticated users to have read-only access to the API.
- The `DjangoObjectPermissions` class ties into Django's standard object permissions framework that allows per-object permissions on models. In order to use this permission class, you'll also need to add a permission backend that supports object-level permissions, such as django-guardian.
  - As with `DjangoModelPermissions`, this permission must only be applied to views that have a `.queryset` property or `.get_queryset()` method. Authorization will only be granted if the user is authenticated and has the relevant per-object permissions and relevant model permissions assigned.
  - `POST` requests require the user to have the add permission on the model instance.
  - `PUT` and PATCH requests require the user to have the change permission on the model instance.
  - `DELETE` requests require the user to have the delete permission on the model instance


# Additional Resources
- [Classy Django REST Framework](http://www.cdrf.co/)
- [Django REST Framework Generic Views](https://www.django-rest-framework.org/api-guide/generic-views/)
