# [JSON Web Tokens](https://jwt.io/introduction/)
- JSON Web Token (JWT) is an open standard (RFC 7519) that defines a compact and self-contained way for securely transmitting information between parties as a JSON object. This information can be verified and trusted because it is digitally signed. JWTs can be signed using a secret (with the HMAC algorithm) or a public/private key pair using RSA or ECDSA.
- Signed tokens can verify the integrity of the claims contained within it, while encrypted tokens hide those claims from other parties. When tokens are signed using public/private key pairs, the signature also certifies that only the party holding the private key is the one that signed it.
- Authorization is the most common scenario for using JWT. Once the user is logged in, each subsequent request will include the JWT, allowing the user to access routes, services, and resources that are permitted with that token.
- JSON Web Tokens are a good way of securely transmitting information between parties. Because JWTs can be signed—for example, using public/private key pairs—you can be sure the senders are who they say they are. Additionally, as the signature is calculated using the header and the payload, you can also verify that the content hasn't been tampered with.
- In its compact form, JSON Web Tokens consist of a header, payload, and signature separated by dots
  - `xxxxx.yyyyy.zzzzz`
- The header typically consists of two parts: the type of the token, which is JWT, and the signing algorithm being used, such as HMAC SHA256 or RSA
  - Then, this JSON is **Base64Url** encoded to form the first part of the JWT.
- The payload contains the claims which are statements about an entity (typically, the user) and additional data. There are three types of claims: 
  - Registered claims are a set of predefined claims which are not mandatory but recommended, to provide a set of useful, interoperable claims.
  - Public claims can be defined at will by those using JWTs. But to avoid collisions they should be defined in the IANA JSON Web Token Registry or be defined as a URI that contains a collision resistant namespace.
  - Private claims are the custom claims created to share information between parties that agree on using them and are neither registered or public claims.
  - The payload is then Base64Url encoded to form the second part of the JSON Web Token.
- To create the signature part you have to take the encoded header, the encoded payload, a secret, the algorithm specified in the header, and sign that. 
- The output is three Base64-URL strings separated by dots that can be easily passed in HTML and HTTP environments, while being more compact when compared to XML-based standards such as SAML.

### How do JSON Web Tokens work?
- In authentication, when the user successfully logs in using their credentials, a JSON Web Token will be returned. Since tokens are credentials, great care must be taken to prevent security issues. In general, you should not keep tokens longer than required.
- Whenever the user wants to access a protected route or resource, the user agent should send the JWT, typically in the Authorization header using the Bearer schema.
- The server's protected routes will check for a valid JWT in the Authorization header, and if it's present, the user will be allowed to access protected resources. If the JWT contains the necessary data, the need to query the database for certain operations may be reduced.



# [DRF JWT Authentication](https://simpleisbetterthancomplex.com/tutorial/2018/12/19/how-to-use-jwt-authentication-with-django-rest-framework.html)
- The JWT is acquired by exchanging an username + password for an access token and an refresh token.
- The access token is usually short-lived (expires in 5 min or so, can be customized though).
- The refresh token lives a little bit longer (expires in 24 hours, also customizable). It is comparable to an authentication session. After it expires, you need a full login with username + password again.
- `pip install djangorestframework_simplejwt`

```
settings.py

REST_FRAMEWORK = {
  'DEFAULT_AUTHENTICATION_CLASSES': [
      'rest_framework_simplejwt.authentication.JWTAuthentication',
  ],
}
```

```
urls.py

from django.urls import path
from rest_framework_simplejwt import views as jwt_views

urlpatterns = [
    # Your URLs...
    path('api/token/', jwt_views.TokenObtainPairView.as_view(), name='token_obtain_pair'),
    path('api/token/refresh/', jwt_views.TokenRefreshView.as_view(), name='token_refresh'),
]
```

```
views.py

from rest_framework.views import APIView
from rest_framework.response import Response
from rest_framework.permissions import IsAuthenticated


class HelloView(APIView):
    permission_classes = (IsAuthenticated,)

    def get(self, request):
        content = {'message': 'Hello, World!'}
        return Response(content)
```

```
urls.py

from django.urls import path
from myapi.core import views

urlpatterns = [
    path('hello/', views.HelloView.as_view(), name='hello'),
]
```




# Additional Resources
- [JWT with DRF - Video](https://www.youtube.com/watch?v=Fhcn2qx-4VQ&ab_channel=PrettyPrinted)
- [Django Migrations Primer](https://realpython.com/django-migrations-a-primer/)