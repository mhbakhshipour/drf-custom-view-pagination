# DRF custom view pagination


## Getting started

This repository contains a utility function prepare_response that can be used to prepare_response in
ViewSet, action vieset and etc... .

## Introduction

When you want to return response in viewset , you can be useful to return response with DRF pagination.

## Installation

```
clone the project
```

## Usage

To use the prepare_response utility, follow these steps:

1. Import the prepare_response function into your view:
```
from utils.response import prepare_response
```
2. Use this in your Viewsets:
```
from rest_framework.viewsets import ViewSet
from rest_framework.decorators import action


class ViewSet(ViewSet):
    ...
    @action(detail=False, methods=["GET"])
        def get_data(self, request):
            has_pagination = request.GET.get("has_pagination", "true") != "false"
            ...

            queryset = Model.objects.filter(is_active=True).order_by("-id")
            response = prepare_response(queryset=queryset, request=request, serializer=ModelSerializer,
                                        is_serializer_many=True, has_pagination=has_pagination)
            return response

```

## Contributing

Contributions to this repository are welcome. If you find any issues or have suggestions for improvement, please open an issue or submit a pull request.