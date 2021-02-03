---
title: Kimliğe göre bir abonelik alma
description: Müşteri KIMLIĞIYLE ve abonelik KIMLIĞIYLE eşleşen bir abonelik kaynağını alır.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 6690a6886eeb31a78cdb556280d4bdc2b4beb124
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769628"
---
# <a name="get-a-subscription-by-id"></a><span data-ttu-id="607a5-103">Kimliğe göre bir abonelik alma</span><span class="sxs-lookup"><span data-stu-id="607a5-103">Get a subscription by ID</span></span>

<span data-ttu-id="607a5-104">**Uygulama hedefi**</span><span class="sxs-lookup"><span data-stu-id="607a5-104">**Applies To**</span></span>

- <span data-ttu-id="607a5-105">İş Ortağı Merkezi</span><span class="sxs-lookup"><span data-stu-id="607a5-105">Partner Center</span></span>
- <span data-ttu-id="607a5-106">21Vianet tarafından çalıştırılan iş ortağı Merkezi</span><span class="sxs-lookup"><span data-stu-id="607a5-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="607a5-107">Microsoft Bulut Almanya için İş Ortağı Merkezi</span><span class="sxs-lookup"><span data-stu-id="607a5-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="607a5-108">Microsoft Cloud for US Government için İş Ortağı Merkezi</span><span class="sxs-lookup"><span data-stu-id="607a5-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="607a5-109">Müşteri KIMLIĞIYLE ve abonelik KIMLIĞIYLE eşleşen bir [abonelik](subscription-resources.md) kaynağını alır.</span><span class="sxs-lookup"><span data-stu-id="607a5-109">Gets a [Subscription](subscription-resources.md) resource that matches the customer ID and the subscription ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="607a5-110">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="607a5-110">Prerequisites</span></span>

- <span data-ttu-id="607a5-111">[Iş ortağı merkezi kimlik doğrulamasında](partner-center-authentication.md)açıklandığı gibi kimlik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="607a5-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="607a5-112">Bu senaryo, hem tek başına uygulama hem de uygulama + kullanıcı kimlik bilgileriyle kimlik doğrulamayı destekler.</span><span class="sxs-lookup"><span data-stu-id="607a5-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="607a5-113">Bir müşteri KIMLIĞI ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="607a5-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="607a5-114">Müşterinin KIMLIĞINI bilmiyorsanız Iş Ortağı Merkezi [panosunda](https://partner.microsoft.com/dashboard)bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="607a5-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="607a5-115">Iş Ortağı Merkezi menüsünden **CSP** ' yi ve ardından **müşteriler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="607a5-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="607a5-116">Müşteri listesinden müşteriyi seçin ve ardından **Hesap**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="607a5-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="607a5-117">Müşterinin hesap sayfasında, **müşteri hesabı bilgileri** bölümünde **Microsoft kimliği** ' ni arayın.</span><span class="sxs-lookup"><span data-stu-id="607a5-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="607a5-118">Microsoft KIMLIĞI, müşteri KIMLIĞI () ile aynıdır `customer-tenant-id` .</span><span class="sxs-lookup"><span data-stu-id="607a5-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="607a5-119">Abonelik KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="607a5-119">A subscription ID.</span></span>

## <a name="c"></a><span data-ttu-id="607a5-120">C\#</span><span class="sxs-lookup"><span data-stu-id="607a5-120">C\#</span></span>

<span data-ttu-id="607a5-121">KIMLIĞE göre abonelik almak için, müşteriyi tanımlamak için müşteri KIMLIĞIYLE [**ıaggregatepartner. Customers. Byıd**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) yöntemini ve aboneliği tanımlamak için [**abonelikler. byıd**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) yöntemini çağırarak abonelik işlemlerine bir arabirim edinerek başlayın.</span><span class="sxs-lookup"><span data-stu-id="607a5-121">To get a subscription by ID, begin by obtaining an interface to the subscription operations by calling the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer, and the [**Subscriptions.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method to identify the subscription.</span></span> <span data-ttu-id="607a5-122">[**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.get)yöntemini çağırarak abonelik ayrıntılarını almak için bu [**arabirimi**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription) kullanın.</span><span class="sxs-lookup"><span data-stu-id="607a5-122">Use that [**interface**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription) to retrieve the subscription details by calling [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.get).</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// string subscriptionID;

var subscriptionDetails = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(subscriptionID).Get();
```

<span data-ttu-id="607a5-123">**Örnek**: [konsol test uygulaması](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="607a5-123">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="607a5-124">**Proje**: Iş Ortağı Merkezi SDK örnekleri **sınıfı**: GetSubscription.cs</span><span class="sxs-lookup"><span data-stu-id="607a5-124">**Project**: Partner Center SDK Samples **Class**: GetSubscription.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="607a5-125">REST isteği</span><span class="sxs-lookup"><span data-stu-id="607a5-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="607a5-126">İstek sözdizimi</span><span class="sxs-lookup"><span data-stu-id="607a5-126">Request syntax</span></span>

| <span data-ttu-id="607a5-127">Yöntem</span><span class="sxs-lookup"><span data-stu-id="607a5-127">Method</span></span>  | <span data-ttu-id="607a5-128">İstek URI'si</span><span class="sxs-lookup"><span data-stu-id="607a5-128">Request URI</span></span>                                                                                                                |
|---------|----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="607a5-129">**Al**</span><span class="sxs-lookup"><span data-stu-id="607a5-129">**GET**</span></span> | <span data-ttu-id="607a5-130">[*{BaseUrl}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-ID}/Subscriptions/{ID-for-Subscription} http/1.1</span><span class="sxs-lookup"><span data-stu-id="607a5-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="607a5-131">URI parametresi</span><span class="sxs-lookup"><span data-stu-id="607a5-131">URI parameter</span></span>

<span data-ttu-id="607a5-132">Bu tablo, aboneliği almak için gerekli sorgu parametrelerini listeler.</span><span class="sxs-lookup"><span data-stu-id="607a5-132">This table lists the required query parameters to get the subscription.</span></span>

| <span data-ttu-id="607a5-133">Ad</span><span class="sxs-lookup"><span data-stu-id="607a5-133">Name</span></span>                    | <span data-ttu-id="607a5-134">Tür</span><span class="sxs-lookup"><span data-stu-id="607a5-134">Type</span></span>     | <span data-ttu-id="607a5-135">Gerekli</span><span class="sxs-lookup"><span data-stu-id="607a5-135">Required</span></span> | <span data-ttu-id="607a5-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="607a5-136">Description</span></span>                               |
|-------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="607a5-137">**Müşteri-Kiracı kimliği**</span><span class="sxs-lookup"><span data-stu-id="607a5-137">**customer-tenant-id**</span></span>  | <span data-ttu-id="607a5-138">**guid**</span><span class="sxs-lookup"><span data-stu-id="607a5-138">**guid**</span></span> | <span data-ttu-id="607a5-139">Y</span><span class="sxs-lookup"><span data-stu-id="607a5-139">Y</span></span>        | <span data-ttu-id="607a5-140">Müşteriye karşılık gelen bir GUID.</span><span class="sxs-lookup"><span data-stu-id="607a5-140">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="607a5-141">**abonelik kimliği**</span><span class="sxs-lookup"><span data-stu-id="607a5-141">**id-for-subscription**</span></span> | <span data-ttu-id="607a5-142">**guid**</span><span class="sxs-lookup"><span data-stu-id="607a5-142">**guid**</span></span> | <span data-ttu-id="607a5-143">Y</span><span class="sxs-lookup"><span data-stu-id="607a5-143">Y</span></span>        | <span data-ttu-id="607a5-144">Aboneliğe karşılık gelen bir GUID.</span><span class="sxs-lookup"><span data-stu-id="607a5-144">A GUID corresponding to the subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="607a5-145">İstek üst bilgileri</span><span class="sxs-lookup"><span data-stu-id="607a5-145">Request headers</span></span>

<span data-ttu-id="607a5-146">Daha fazla bilgi için bkz. [Iş ortağı MERKEZI Rest üstbilgileri](headers.md).</span><span class="sxs-lookup"><span data-stu-id="607a5-146">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="607a5-147">İstek gövdesi</span><span class="sxs-lookup"><span data-stu-id="607a5-147">Request body</span></span>

<span data-ttu-id="607a5-148">Yok.</span><span class="sxs-lookup"><span data-stu-id="607a5-148">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="607a5-149">İstek örneği</span><span class="sxs-lookup"><span data-stu-id="607a5-149">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/subscriptions/A356AC8C-E310-44F4-BF85-C7F29044AF99 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 8f489776-a3f3-47cb-91c3-538e1f70f560
MS-CorrelationId: e72e1dc3-4abd-4ce0-908b-d23fdaedcb28
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="607a5-150">REST yanıtı</span><span class="sxs-lookup"><span data-stu-id="607a5-150">REST response</span></span>

<span data-ttu-id="607a5-151">Başarılı olursa, bu yöntem yanıt gövdesinde bir [abonelik](subscription-resources.md) kaynağı döndürür.</span><span class="sxs-lookup"><span data-stu-id="607a5-151">If successful, this method returns a [Subscription](subscription-resources.md) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="607a5-152">Yanıt başarısı ve hata kodları</span><span class="sxs-lookup"><span data-stu-id="607a5-152">Response success and error codes</span></span>

<span data-ttu-id="607a5-153">Her yanıt başarı veya başarısızlık ve ek hata ayıklama bilgilerini gösteren bir HTTP durum kodu ile gelir.</span><span class="sxs-lookup"><span data-stu-id="607a5-153">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="607a5-154">Bu kodu, hata türünü ve ek parametreleri okumak için bir ağ izleme aracı kullanın.</span><span class="sxs-lookup"><span data-stu-id="607a5-154">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="607a5-155">Tam liste için bkz. [Iş ortağı MERKEZI Rest hata kodları](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="607a5-155">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example-for-a-standard-subscription"></a><span data-ttu-id="607a5-156">Standart abonelik için yanıt örneği</span><span class="sxs-lookup"><span data-stu-id="607a5-156">Response example for a standard subscription</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 833
Content-Type: application/json; charset=utf-8
MS-CorrelationId: e72e1dc3-4abd-4ce0-908b-d23fdaedcb28
MS-RequestId: 8f489776-a3f3-47cb-91c3-538e1f70f560
MS-CV: 7v11Wa//5EuGEo+A.0
MS-ServerId: 202010406
Date: Fri, 27 Jan 2017 21:51:40 GMT

{
    "id": "A356AC8C-E310-44F4-BF85-C7F29044AF99",
    "entitlementId": "42226ED6-070A-4E0F-B80C-4CDFB3E97AA7",
    "offerId": "MS-AZR-0145P",
    "offerName": "Microsoft Azure",
    "friendlyName": "Microsoft Azure",
    "quantity": 1,
    "unitType": "Usage-based",
    "creationDate": "2016-05-10T07:30:05.427Z",
    "effectiveStartDate": "2016-05-10T00:00:00Z",
    "commitmentEndDate": "9999-12-10T00:00:00Z",
    "status": "active",
    "autoRenewEnabled": false,
    "billingType": "usage",
    "contractType": "subscription",
    "links": {
        "offer": {
            "uri": "/offers/MS-AZR-0145P?country=US",
            "method": "GET",
            "headers": []
        },
        "self": {
            "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/subscriptions/A356AC8C-E310-44F4-BF85-C7F29044AF99",
            "method": "GET",
            "headers": []
        }
    },
    "orderId": "B23FDEDD-D6BD-415A-8B71-3624C81C9644",
    "attributes": {
        "etag": "eyJpZCI6ImEzNTZhYzhjLWUzMTAtNDRmNC1iZjg1LWM3ZjI5MDQ0YWY5OSIsInZlcnNpb24iOjJ9",
        "objectType": "Subscription"
    }
}
```

### <a name="response-example-for-an-add-on-subscription"></a><span data-ttu-id="607a5-157">Eklenti aboneliği için yanıt örneği</span><span class="sxs-lookup"><span data-stu-id="607a5-157">Response example for an add-on subscription</span></span>

<span data-ttu-id="607a5-158">Bir eklenti aboneliğine yönelik yanıt, gövdedeki ve bağlantılardaki üst abonelik KIMLIĞINI içerir.</span><span class="sxs-lookup"><span data-stu-id="607a5-158">The response for an add-on subscription includes the parent subscription ID in the body and in the links.</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1132
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 6eacec93-852d-4167-9d96-c57809bea7ed
MS-RequestId: 22bfd0fb-d1e6-4a8f-aa1a-124b7c820d80
MS-CV: cmde2DtbuUWi8JLq.0
MS-ServerId: 201022015
Date: Fri, 27 Jan 2017 00:12:53 GMT

{
    "id": "968BA1CF-C146-4ADF-A300-308DCF718EEE",
    "offerId": "2828BE95-46BA-4F91-B2FD-0BEF192ECF60",
    "offerName": "Exchange Online Archiving for Exchange Online",
    "friendlyName": "Some friendly name",
    "quantity": 2,
    "unitType": "Licenses",
    "parentSubscriptionId": "1C2B75C1-74A5-472A-A729-7F8CEFC477F9",
    "creationDate": "2017-01-25T23:01:08.693Z",
    "effectiveStartDate": "2017-01-25T00:00:00Z",
    "commitmentEndDate": "2018-02-10T00:00:00Z",
    "status": "active",
    "autoRenewEnabled": true,
    "billingType": "license",
    "contractType": "subscription",
    "links": {
        "offer": {
            "uri": "/offers/2828BE95-46BA-4F91-B2FD-0BEF192ECF60?country=US",
            "method": "GET",
            "headers": []
        },
        "parentSubscription": {
            "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/subscriptions/1C2B75C1-74A5-472A-A729-7F8CEFC477F9",
            "method": "GET",
            "headers": []
        },
        "self": {
            "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/subscriptions/968BA1CF-C146-4ADF-A300-308DCF718EEE",
            "method": "GET",
            "headers": []
        }
    },
    "orderId": "CF3B0E37-BE0B-4CDD-B584-D1A97D98A922",
    "attributes": {
        "etag": "eyJpZCI6Ijk2OGJhMWNmLWMxNDYtNGFkZi1hMzAwLTMwOGRjZjcxOGVlZSIsInZlcnNpb24iOjF9",
        "objectType": "Subscription"
    }
}
```
