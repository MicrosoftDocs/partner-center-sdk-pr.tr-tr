---
title: Müşterinin kullanıcı hesabını silme
description: Bir müşterinin mevcut kullanıcı hesabını silme.
ms.date: 06/20/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c45646da43b8926f911942374de5da07f318c526
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973069"
---
# <a name="delete-a-user-account-for-a-customer"></a><span data-ttu-id="27b6a-103">Müşterinin kullanıcı hesabını silme</span><span class="sxs-lookup"><span data-stu-id="27b6a-103">Delete a user account for a customer</span></span>

<span data-ttu-id="27b6a-104">Bu makalede, bir müşterinin mevcut kullanıcı hesabının nasıl silineceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="27b6a-104">This article explains how to delete an existing user account for a customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="27b6a-105">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="27b6a-105">Prerequisites</span></span>

- <span data-ttu-id="27b6a-106">[Iş ortağı merkezi kimlik doğrulamasında](partner-center-authentication.md)açıklandığı gibi kimlik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="27b6a-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="27b6a-107">Bu senaryo yalnızca uygulama + kullanıcı kimlik bilgileriyle kimlik doğrulamayı destekler.</span><span class="sxs-lookup"><span data-stu-id="27b6a-107">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="27b6a-108">Bir müşteri KIMLIĞI ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="27b6a-108">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="27b6a-109">Müşterinin KIMLIĞINI bilmiyorsanız Iş Ortağı Merkezi [panosunda](https://partner.microsoft.com/dashboard)bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27b6a-109">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="27b6a-110">Iş Ortağı Merkezi menüsünden **CSP** ' yi ve ardından **müşteriler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="27b6a-110">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="27b6a-111">Müşteri listesinden müşteriyi seçin ve ardından **Hesap**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="27b6a-111">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="27b6a-112">Müşterinin hesap sayfasında, **müşteri hesabı bilgileri** bölümünde **Microsoft kimliği** ' ni arayın.</span><span class="sxs-lookup"><span data-stu-id="27b6a-112">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="27b6a-113">Microsoft KIMLIĞI, müşteri KIMLIĞI () ile aynıdır `customer-tenant-id` .</span><span class="sxs-lookup"><span data-stu-id="27b6a-113">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="27b6a-114">Bir kullanıcı KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="27b6a-114">A user ID.</span></span> <span data-ttu-id="27b6a-115">Kullanıcı KIMLIĞINIZ yoksa, bkz. [bir müşterinin tüm Kullanıcı hesaplarının listesini alın](get-a-list-of-all-user-accounts-for-a-customer.md).</span><span class="sxs-lookup"><span data-stu-id="27b6a-115">If you do not have the user ID, see [Get a list of all user accounts for a customer](get-a-list-of-all-user-accounts-for-a-customer.md).</span></span>

## <a name="deleting-a-user-account"></a><span data-ttu-id="27b6a-116">Kullanıcı hesabını silme</span><span class="sxs-lookup"><span data-stu-id="27b6a-116">Deleting a user account</span></span>

<span data-ttu-id="27b6a-117">Bir kullanıcı hesabını sildiğinizde, Kullanıcı durumu 30 gün boyunca **etkin değil** olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="27b6a-117">When you delete a user account, the user state is set to **inactive** for 30 days.</span></span> <span data-ttu-id="27b6a-118">30 30 gün sonra, Kullanıcı hesabı ve onunla ilişkili veriler temizlenir ve kurtarılamaz hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="27b6a-118">After thirty 30 days, the user account and its associated data are purged and made unrecoverable.</span></span>

<span data-ttu-id="27b6a-119">Etkin olmayan hesap 30 günlük bir pencere içindeyse, [bir müşterinin silinen kullanıcı hesabını geri yükleyebilirsiniz](restore-a-user-for-a-customer.md) .</span><span class="sxs-lookup"><span data-stu-id="27b6a-119">You can [restore a deleted user account for a customer](restore-a-user-for-a-customer.md) if the inactive account is within the 30-day window.</span></span> <span data-ttu-id="27b6a-120">Ancak, silinmiş ve devre dışı olarak işaretlenen bir hesabı geri yüklediğinizde, hesap artık kullanıcı koleksiyonunun bir üyesi olarak döndürülmez (örneğin, [bir müşterinin tüm Kullanıcı hesaplarının bir listesini](get-a-list-of-all-user-accounts-for-a-customer.md)aldığınızda).</span><span class="sxs-lookup"><span data-stu-id="27b6a-120">However, when you restore an account that was deleted and marked as inactive, the account is no longer returned as a member of the user collection (for example, when you [get a list of all user accounts for a customer](get-a-list-of-all-user-accounts-for-a-customer.md)).</span></span>

## <a name="c"></a><span data-ttu-id="27b6a-121">C\#</span><span class="sxs-lookup"><span data-stu-id="27b6a-121">C\#</span></span>

<span data-ttu-id="27b6a-122">Mevcut bir müşteri Kullanıcı hesabını silmek için:</span><span class="sxs-lookup"><span data-stu-id="27b6a-122">To delete an existing customer user account:</span></span>

1. <span data-ttu-id="27b6a-123">Müşteriyi tanımlamak için, müşteri KIMLIĞIYLE [**ıaggregatepartner. Customers. Byıd**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="27b6a-123">Use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span>

2. <span data-ttu-id="27b6a-124">Kullanıcıyı tanımlamak için [**Users. Byıd**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) metodunu çağırın.</span><span class="sxs-lookup"><span data-stu-id="27b6a-124">Call the [**Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method to identify the user.</span></span>

3. <span data-ttu-id="27b6a-125">Kullanıcıyı silmek ve Kullanıcı durumunu devre dışı olarak ayarlamak için [**silme**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.delete) yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="27b6a-125">Call the [**Delete**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.delete) method to delete the user and set the user state to inactive.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// string customerUserIdToDelete;

partnerOperations.Customers.ById(selectedCustomerId).Users.ById(customerUserIdToDelete).Delete();
```

<span data-ttu-id="27b6a-126">**Örnek**: [konsol test uygulaması](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="27b6a-126">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="27b6a-127">**Project**: iş ortağı merkezi SDK örnekleri **sınıfı**: deletecustomeruser. cs</span><span class="sxs-lookup"><span data-stu-id="27b6a-127">**Project**: Partner Center SDK Samples **Class**: DeleteCustomerUser.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="27b6a-128">REST isteği</span><span class="sxs-lookup"><span data-stu-id="27b6a-128">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="27b6a-129">İstek sözdizimi</span><span class="sxs-lookup"><span data-stu-id="27b6a-129">Request syntax</span></span>

| <span data-ttu-id="27b6a-130">Yöntem</span><span class="sxs-lookup"><span data-stu-id="27b6a-130">Method</span></span>     | <span data-ttu-id="27b6a-131">İstek URI'si</span><span class="sxs-lookup"><span data-stu-id="27b6a-131">Request URI</span></span>                                                                                            |
|------------|--------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="27b6a-132">DELETE</span><span class="sxs-lookup"><span data-stu-id="27b6a-132">DELETE</span></span>     | <span data-ttu-id="27b6a-133">[*{BaseUrl}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-ID}/Users/{User-ID} http/1.1</span><span class="sxs-lookup"><span data-stu-id="27b6a-133">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users/{user-id} HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="27b6a-134">URI parametreleri</span><span class="sxs-lookup"><span data-stu-id="27b6a-134">URI parameters</span></span>

<span data-ttu-id="27b6a-135">Müşteriyi ve kullanıcıyı tanımlamak için aşağıdaki sorgu parametrelerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="27b6a-135">Use the following query parameters to identify the customer and user.</span></span>

| <span data-ttu-id="27b6a-136">Ad</span><span class="sxs-lookup"><span data-stu-id="27b6a-136">Name</span></span>                   | <span data-ttu-id="27b6a-137">Tür</span><span class="sxs-lookup"><span data-stu-id="27b6a-137">Type</span></span>     | <span data-ttu-id="27b6a-138">Gerekli</span><span class="sxs-lookup"><span data-stu-id="27b6a-138">Required</span></span> | <span data-ttu-id="27b6a-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27b6a-139">Description</span></span>                                                                                                               |
|------------------------|----------|----------|---------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="27b6a-140">Müşteri-Kiracı kimliği</span><span class="sxs-lookup"><span data-stu-id="27b6a-140">customer-tenant-id</span></span>     | <span data-ttu-id="27b6a-141">GUID</span><span class="sxs-lookup"><span data-stu-id="27b6a-141">GUID</span></span>     | <span data-ttu-id="27b6a-142">Y</span><span class="sxs-lookup"><span data-stu-id="27b6a-142">Y</span></span>        | <span data-ttu-id="27b6a-143">Değer, satıcının belirli bir müşteriye ait sonuçları filtrelemesine olanak tanıyan bir GUID biçimli **Müşteri-kiracı kimliğidir** .</span><span class="sxs-lookup"><span data-stu-id="27b6a-143">The value is a GUID-formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer.</span></span> |
| <span data-ttu-id="27b6a-144">user-id</span><span class="sxs-lookup"><span data-stu-id="27b6a-144">user-id</span></span>                | <span data-ttu-id="27b6a-145">GUID</span><span class="sxs-lookup"><span data-stu-id="27b6a-145">GUID</span></span>     | <span data-ttu-id="27b6a-146">Y</span><span class="sxs-lookup"><span data-stu-id="27b6a-146">Y</span></span>        | <span data-ttu-id="27b6a-147">Değer, tek bir kullanıcı hesabına ait olan GUID biçimli bir **Kullanıcı kimliğidir** .</span><span class="sxs-lookup"><span data-stu-id="27b6a-147">The value is a GUID-formatted **user-id** that belongs to a single user account.</span></span>                                          |

### <a name="request-headers"></a><span data-ttu-id="27b6a-148">İstek üst bilgileri</span><span class="sxs-lookup"><span data-stu-id="27b6a-148">Request headers</span></span>

<span data-ttu-id="27b6a-149">Daha fazla bilgi için bkz. [Iş ortağı MERKEZI Rest üstbilgileri](headers.md).</span><span class="sxs-lookup"><span data-stu-id="27b6a-149">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="27b6a-150">İstek gövdesi</span><span class="sxs-lookup"><span data-stu-id="27b6a-150">Request body</span></span>

<span data-ttu-id="27b6a-151">Yok.</span><span class="sxs-lookup"><span data-stu-id="27b6a-151">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="27b6a-152">İstek örneği</span><span class="sxs-lookup"><span data-stu-id="27b6a-152">Request example</span></span>

```http
DELETE https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users/a45f1416-3300-4f65-9e8d-f123b397a4ea HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: f113b126-ec13-4baa-ab4d-67c245244971
MS-CorrelationId: 709c0b80-016c-4662-b29f-697fdf03e87a
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Content-Length: 0
```

## <a name="rest-response"></a><span data-ttu-id="27b6a-153">REST yanıtı</span><span class="sxs-lookup"><span data-stu-id="27b6a-153">REST response</span></span>

<span data-ttu-id="27b6a-154">Başarılı olursa, bu yöntem bir **204 içerik** durum kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="27b6a-154">If successful, this method returns a **204 No Content** status code.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="27b6a-155">Yanıt başarısı ve hata kodları</span><span class="sxs-lookup"><span data-stu-id="27b6a-155">Response success and error codes</span></span>

<span data-ttu-id="27b6a-156">Her yanıt başarı veya başarısızlık ve ek hata ayıklama bilgilerini gösteren bir HTTP durum kodu ile gelir.</span><span class="sxs-lookup"><span data-stu-id="27b6a-156">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="27b6a-157">Bu kodu, hata türünü ve ek parametreleri okumak için bir ağ izleme aracı kullanın.</span><span class="sxs-lookup"><span data-stu-id="27b6a-157">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="27b6a-158">Tam liste için bkz. [Iş ortağı MERKEZI Rest hata kodları](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="27b6a-158">For the full list, see [Partner Center REST Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="27b6a-159">Yanıt örneği</span><span class="sxs-lookup"><span data-stu-id="27b6a-159">Response example</span></span>

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: 709c0b80-016c-4662-b29f-697fdf03e87a
MS-RequestId: f113b126-ec13-4baa-ab4d-67c245244971
MS-CV: 90KUJA7HKEaG8wHu.0
MS-ServerId: 101112616
Date: Tue, 24 Jan 2017 23:27:18 GMT
```
