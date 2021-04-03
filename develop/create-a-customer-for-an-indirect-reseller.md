---
title: Dolaylı satıcı için müşteri oluşturma
description: Dolaylı bir sağlayıcının dolaylı bir satıcı için müşteri oluşturmak üzere Iş Ortağı Merkezi API 'Lerini nasıl kullanabileceği hakkında bilgi edinin.
ms.date: 03/30/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 13cd1b051abb536d397dcd4000228f67fe3206b8
ms.sourcegitcommit: 204e518e794b6b076a17488ee9ca1aaaa4beaaec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2021
ms.locfileid: "106103955"
---
# <a name="create-a-customer-for-an-indirect-reseller-using-partner-center-apis"></a><span data-ttu-id="3e2ca-103">Iş Ortağı Merkezi API 'Lerini kullanarak dolaylı satıcı için müşteri oluşturma</span><span class="sxs-lookup"><span data-stu-id="3e2ca-103">Create a customer for an indirect reseller using Partner Center APIs</span></span>

<span data-ttu-id="3e2ca-104">**Uygulama hedefi:**</span><span class="sxs-lookup"><span data-stu-id="3e2ca-104">**Applies to:**</span></span>

- <span data-ttu-id="3e2ca-105">İş Ortağı Merkezi</span><span class="sxs-lookup"><span data-stu-id="3e2ca-105">Partner Center</span></span>

<span data-ttu-id="3e2ca-106">Dolaylı bir sağlayıcı, dolaylı bir satıcı için müşteri oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="3e2ca-106">An indirect provider can create a customer for an indirect reseller.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3e2ca-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="3e2ca-107">Prerequisites</span></span>

- <span data-ttu-id="3e2ca-108">[Iş ortağı merkezi kimlik doğrulamasında](partner-center-authentication.md)açıklandığı gibi kimlik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="3e2ca-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="3e2ca-109">Bu senaryo yalnızca uygulama + kullanıcı kimlik bilgileriyle kimlik doğrulamayı destekler.</span><span class="sxs-lookup"><span data-stu-id="3e2ca-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="3e2ca-110">Dolaylı Bayi kiracı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="3e2ca-110">The tenant identifier of the indirect reseller.</span></span>

- <span data-ttu-id="3e2ca-111">Dolaylı satıcının dolaylı sağlayıcıyla bir ortaklığı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e2ca-111">The indirect reseller must have a partnership with the indirect provider.</span></span>

## <a name="c"></a><span data-ttu-id="3e2ca-112">C\#</span><span class="sxs-lookup"><span data-stu-id="3e2ca-112">C\#</span></span>

<span data-ttu-id="3e2ca-113">Dolaylı bir satıcı için yeni bir müşteri eklemek için:</span><span class="sxs-lookup"><span data-stu-id="3e2ca-113">To add a new customer for an indirect reseller:</span></span>

1. <span data-ttu-id="3e2ca-114">Yeni bir [**Müşteri**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer) nesnesi örneği oluşturun ve ardından [**Billingprofile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerbillingprofile) ve [**companyprofile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customercompanyprofile)öğesini oluşturup doldurun.</span><span class="sxs-lookup"><span data-stu-id="3e2ca-114">Instantiate a new [**Customer**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer) object and then instantiate and populate the [**BillingProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerbillingprofile) and [**CompanyProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customercompanyprofile).</span></span> <span data-ttu-id="3e2ca-115">Dolaylı satıcı KIMLIĞINI [**ilişkili Iş ortağı kimliği**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer.associatedpartnerid) özelliğine atadığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="3e2ca-115">Be sure to assign the indirect reseller ID to the [**AssociatedPartnerID**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer.associatedpartnerid) property.</span></span>

2. <span data-ttu-id="3e2ca-116">Müşteri koleksiyonu işlemlerine bir arabirim almak için [**ıaggregatepartner. Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e2ca-116">Use the [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) property to get an interface to customer collection operations.</span></span>

3. <span data-ttu-id="3e2ca-117">Müşteriyi oluşturmak için [**Create**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.create) veya [**createasync**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.createasync) metodunu çağırın.</span><span class="sxs-lookup"><span data-stu-id="3e2ca-117">Call the [**Create**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.createasync) method to create the customer.</span></span>

### <a name="c-example"></a><span data-ttu-id="3e2ca-118">C \# örneği</span><span class="sxs-lookup"><span data-stu-id="3e2ca-118">C\# example</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var indirectResellerId;
var customerToCreate = new Customer()
{
    CompanyProfile = new CustomerCompanyProfile()
    {
        Domain = string.Format(CultureInfo.InvariantCulture,
            "WingtipToys{0}.{1}",
            new Random().Next(),
            this.Context.Configuration.Scenario.CustomerDomainSuffix)
    },
    BillingProfile = new CustomerBillingProfile()
    {
        Culture = "EN-US",
        Email = "Gena@wingtiptoys.com",
        Language = "En",
        CompanyName = "Wingtip Toys" + new Random().Next(),
        DefaultAddress = new Address()
        {
            FirstName = "Gena",
            LastName = "Soto",
            AddressLine1 = "One Microsoft Way",
            City = "Redmond",
            State = "WA",
            Country = "US",
            PostalCode = "98052",
            PhoneNumber = "4255550101"
        }
    },
    AssociatedPartnerId = indirectResellerId
};

var newCustomer = partnerOperations.Customers.Create(customerToCreate);
```

<span data-ttu-id="3e2ca-119">**Örnek**: [konsol test uygulaması](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="3e2ca-119">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="3e2ca-120">**Proje**: Iş Ortağı Merkezi SDK örnekleri **sınıfı**: createcustomerforındirectbayi. cs</span><span class="sxs-lookup"><span data-stu-id="3e2ca-120">**Project**: Partner Center SDK Samples **Class**: CreateCustomerforIndirectReseller.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="3e2ca-121">REST isteği</span><span class="sxs-lookup"><span data-stu-id="3e2ca-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="3e2ca-122">İstek sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3e2ca-122">Request syntax</span></span>

| <span data-ttu-id="3e2ca-123">Yöntem</span><span class="sxs-lookup"><span data-stu-id="3e2ca-123">Method</span></span>   | <span data-ttu-id="3e2ca-124">İstek URI'si</span><span class="sxs-lookup"><span data-stu-id="3e2ca-124">Request URI</span></span>                                                       |
|----------|-------------------------------------------------------------------|
| <span data-ttu-id="3e2ca-125">**Yayınla**</span><span class="sxs-lookup"><span data-stu-id="3e2ca-125">**POST**</span></span> | <span data-ttu-id="3e2ca-126">[*{BaseUrl}*](partner-center-rest-urls.md)/v1/Customers http/1.1</span><span class="sxs-lookup"><span data-stu-id="3e2ca-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="3e2ca-127">İstek üst bilgileri</span><span class="sxs-lookup"><span data-stu-id="3e2ca-127">Request headers</span></span>

<span data-ttu-id="3e2ca-128">Daha fazla bilgi için bkz. [Iş ortağı MERKEZI Rest üstbilgileri](headers.md).</span><span class="sxs-lookup"><span data-stu-id="3e2ca-128">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="3e2ca-129">İstek gövdesi</span><span class="sxs-lookup"><span data-stu-id="3e2ca-129">Request body</span></span>

<span data-ttu-id="3e2ca-130">Bu tabloda, istek gövdesinde gereken özellikler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3e2ca-130">This table describes the required properties in the request body.</span></span>

| <span data-ttu-id="3e2ca-131">Ad</span><span class="sxs-lookup"><span data-stu-id="3e2ca-131">Name</span></span>                                          | <span data-ttu-id="3e2ca-132">Tür</span><span class="sxs-lookup"><span data-stu-id="3e2ca-132">Type</span></span>   | <span data-ttu-id="3e2ca-133">Gerekli</span><span class="sxs-lookup"><span data-stu-id="3e2ca-133">Required</span></span> | <span data-ttu-id="3e2ca-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e2ca-134">Description</span></span>                                                                                                                                                                                                                                                                                                                                           |
|-----------------------------------------------|--------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [<span data-ttu-id="3e2ca-135">BillingProfile</span><span class="sxs-lookup"><span data-stu-id="3e2ca-135">BillingProfile</span></span>](#billing-profile)             | <span data-ttu-id="3e2ca-136">object</span><span class="sxs-lookup"><span data-stu-id="3e2ca-136">object</span></span> | <span data-ttu-id="3e2ca-137">Yes</span><span class="sxs-lookup"><span data-stu-id="3e2ca-137">Yes</span></span>      | <span data-ttu-id="3e2ca-138">Müşterinin Faturalandırma profili bilgileri.</span><span class="sxs-lookup"><span data-stu-id="3e2ca-138">The customer's billing profile information.</span></span>                                                                                                                                                                                                                                                                                                           |
| [<span data-ttu-id="3e2ca-139">CompanyProfile</span><span class="sxs-lookup"><span data-stu-id="3e2ca-139">CompanyProfile</span></span>](#company-profile)             | <span data-ttu-id="3e2ca-140">object</span><span class="sxs-lookup"><span data-stu-id="3e2ca-140">object</span></span> | <span data-ttu-id="3e2ca-141">Yes</span><span class="sxs-lookup"><span data-stu-id="3e2ca-141">Yes</span></span>      | <span data-ttu-id="3e2ca-142">Müşterinin şirket profili bilgileri.</span><span class="sxs-lookup"><span data-stu-id="3e2ca-142">The customer's company profile information.</span></span>                                                               
| [<span data-ttu-id="3e2ca-143">Ilişkili iş ortağı kimliği</span><span class="sxs-lookup"><span data-stu-id="3e2ca-143">AssociatedPartnerId</span></span>](customer-resources.md#customer) | <span data-ttu-id="3e2ca-144">string</span><span class="sxs-lookup"><span data-stu-id="3e2ca-144">string</span></span> | <span data-ttu-id="3e2ca-145">Yes</span><span class="sxs-lookup"><span data-stu-id="3e2ca-145">Yes</span></span>      | <span data-ttu-id="3e2ca-146">Dolaylı satıcı KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="3e2ca-146">The indirect reseller ID.</span></span> <span data-ttu-id="3e2ca-147">Burada sağlanan KIMLIğIN gösterdiği dolaylı satıcının dolaylı sağlayıcıyla bir ortaklığı olmalıdır veya istek başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="3e2ca-147">The indirect reseller as indicated by the ID supplied here must have a partnership with the indirect provider or the request will fail.</span></span> <span data-ttu-id="3e2ca-148">Ayrıca, Ilişkili iş ortağı kimliği değeri sağlanmazsa, müşterinin dolaylı satıcı yerine dolaylı sağlayıcının doğrudan müşterisi olarak oluşturulduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3e2ca-148">Also note that if the AssociatedPartnerId value isn't supplied, the customer is created as a direct customer of the indirect provider rather than the indirect reseller.</span></span> |
|<span data-ttu-id="3e2ca-149">Etki alanı</span><span class="sxs-lookup"><span data-stu-id="3e2ca-149">Domain</span></span>| <span data-ttu-id="3e2ca-150">Dize</span><span class="sxs-lookup"><span data-stu-id="3e2ca-150">String</span></span>| <span data-ttu-id="3e2ca-151">Yes</span><span class="sxs-lookup"><span data-stu-id="3e2ca-151">Yes</span></span>|<span data-ttu-id="3e2ca-152">Müşterinin etki alanı adı, örneğin contoso.onmicrosoft.com.</span><span class="sxs-lookup"><span data-stu-id="3e2ca-152">The customer's domain name, such as contoso.onmicrosoft.com.</span></span>|
|<span data-ttu-id="3e2ca-153">organizationRegistrationNumber</span><span class="sxs-lookup"><span data-stu-id="3e2ca-153">organizationRegistrationNumber</span></span>|    <span data-ttu-id="3e2ca-154">string</span><span class="sxs-lookup"><span data-stu-id="3e2ca-154">string</span></span>|<span data-ttu-id="3e2ca-155">Yes</span><span class="sxs-lookup"><span data-stu-id="3e2ca-155">Yes</span></span>|     <span data-ttu-id="3e2ca-156">Müşterinin kuruluş kayıt numarası (bazı ülkelerde ıNN numarası olarak da adlandırılır).</span><span class="sxs-lookup"><span data-stu-id="3e2ca-156">The customer’s organization registration number (also referred to as INN number in certain countries).</span></span> <span data-ttu-id="3e2ca-157">Yalnızca şu ülkelerde bulunan müşterinin şirketi/kuruluşu için gereklidir: Ermenistan (Har), Azerbaycan (AZ), Belarus (BY), Macaristan (HU), Kazakistan (KZ), Kırgızistan (KG), Moldova (MD), Rusya (RU), Tacikistan dili (TJ), Özbekistan (UZ), Ukrayna (UA), Hindistan, Brezilya, Güney Afrika, Polonya, Birleşik Arap Emirlikleri, Suudi Arabistan, Türkiye, Tayland, Vietnam, Myanmar, Irak, Güney Sudan ve Venezuela.</span><span class="sxs-lookup"><span data-stu-id="3e2ca-157">Only required for customer’s company/organization located in the following countries: Armenia(AM), Azerbaijan(AZ), Belarus(BY), Hungary(HU), Kazakhstan(KZ), Kyrgyzstan(KG), Moldova(MD), Russia(RU), Tajikistan(TJ), Uzbekistan(UZ), Ukraine(UA), India, Brazil, South Africa, Poland, United Arab Emirates, Saudi Arabia, Turkey, Thailand, Vietnam, Myanmar, Iraq, South Sudan and Venezuela.</span></span> <span data-ttu-id="3e2ca-158">Müşterinin veya diğer ülkelerde bulunan şirket/kuruluş için bu, isteğe bağlı bir alandır.</span><span class="sxs-lookup"><span data-stu-id="3e2ca-158">For customer’s company/organization located in other countries this is an optional field.</span></span>|



#### <a name="billing-profile"></a><span data-ttu-id="3e2ca-159">Faturalama profili</span><span class="sxs-lookup"><span data-stu-id="3e2ca-159">Billing profile</span></span>

<span data-ttu-id="3e2ca-160">Bu tabloda, yeni bir müşteri oluşturmak için gereken [Customerbillingprofile](customer-resources.md#customerbillingprofile) kaynağından gereken en düşük alan açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3e2ca-160">This table describes the minimum required fields from the [CustomerBillingProfile](customer-resources.md#customerbillingprofile) resource needed to create a new customer.</span></span>

| <span data-ttu-id="3e2ca-161">Ad</span><span class="sxs-lookup"><span data-stu-id="3e2ca-161">Name</span></span>             | <span data-ttu-id="3e2ca-162">Tür</span><span class="sxs-lookup"><span data-stu-id="3e2ca-162">Type</span></span>                                     | <span data-ttu-id="3e2ca-163">Gerekli</span><span class="sxs-lookup"><span data-stu-id="3e2ca-163">Required</span></span> | <span data-ttu-id="3e2ca-164">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e2ca-164">Description</span></span>                                                                                                                                                                                                     |
|------------------|------------------------------------------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="3e2ca-165">e-posta</span><span class="sxs-lookup"><span data-stu-id="3e2ca-165">email</span></span>            | <span data-ttu-id="3e2ca-166">string</span><span class="sxs-lookup"><span data-stu-id="3e2ca-166">string</span></span>                                   | <span data-ttu-id="3e2ca-167">Yes</span><span class="sxs-lookup"><span data-stu-id="3e2ca-167">Yes</span></span>      | <span data-ttu-id="3e2ca-168">Müşterinin e-posta adresi.</span><span class="sxs-lookup"><span data-stu-id="3e2ca-168">The customer's email address.</span></span>                                                                                                                                                                                   |
| <span data-ttu-id="3e2ca-169">kültür</span><span class="sxs-lookup"><span data-stu-id="3e2ca-169">culture</span></span>          | <span data-ttu-id="3e2ca-170">string</span><span class="sxs-lookup"><span data-stu-id="3e2ca-170">string</span></span>                                   | <span data-ttu-id="3e2ca-171">Yes</span><span class="sxs-lookup"><span data-stu-id="3e2ca-171">Yes</span></span>      | <span data-ttu-id="3e2ca-172">İletişim ve para birimi için tercih edilen kültür, "en-US" gibi.</span><span class="sxs-lookup"><span data-stu-id="3e2ca-172">Their preferred culture for communication and currency, such as "en-US".</span></span> <span data-ttu-id="3e2ca-173">Desteklenen kültürler için [Iş Ortağı Merkezi tarafından desteklenen dillere ve yerel ayarlara](partner-center-supported-languages-and-locales.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="3e2ca-173">See [Partner Center supported languages and locales](partner-center-supported-languages-and-locales.md) for the supported cultures.</span></span> |
| <span data-ttu-id="3e2ca-174">language</span><span class="sxs-lookup"><span data-stu-id="3e2ca-174">language</span></span>         | <span data-ttu-id="3e2ca-175">string</span><span class="sxs-lookup"><span data-stu-id="3e2ca-175">string</span></span>                                   | <span data-ttu-id="3e2ca-176">Yes</span><span class="sxs-lookup"><span data-stu-id="3e2ca-176">Yes</span></span>      | <span data-ttu-id="3e2ca-177">Varsayılan dil.</span><span class="sxs-lookup"><span data-stu-id="3e2ca-177">The default language.</span></span> <span data-ttu-id="3e2ca-178">İki karakter dil kodu (örneğin `en` veya `fr` ) desteklenir.</span><span class="sxs-lookup"><span data-stu-id="3e2ca-178">Two character language codes (for example `en` or `fr`) are supported.</span></span>                                                                                                                                |
| <span data-ttu-id="3e2ca-179">Şirket \_ adı</span><span class="sxs-lookup"><span data-stu-id="3e2ca-179">company\_name</span></span>    | <span data-ttu-id="3e2ca-180">string</span><span class="sxs-lookup"><span data-stu-id="3e2ca-180">string</span></span>                                   | <span data-ttu-id="3e2ca-181">Yes</span><span class="sxs-lookup"><span data-stu-id="3e2ca-181">Yes</span></span>      | <span data-ttu-id="3e2ca-182">Kayıtlı şirket/kuruluş adı.</span><span class="sxs-lookup"><span data-stu-id="3e2ca-182">The registered company/organization name.</span></span>                                                                                                                                                                       |
| <span data-ttu-id="3e2ca-183">Varsayılan \_ Adres</span><span class="sxs-lookup"><span data-stu-id="3e2ca-183">default\_address</span></span> | [<span data-ttu-id="3e2ca-184">Adres</span><span class="sxs-lookup"><span data-stu-id="3e2ca-184">Address</span></span>](utility-resources.md#address) | <span data-ttu-id="3e2ca-185">Yes</span><span class="sxs-lookup"><span data-stu-id="3e2ca-185">Yes</span></span>      | <span data-ttu-id="3e2ca-186">Müşterinin şirketinin/kuruluşunun kayıtlı adresi.</span><span class="sxs-lookup"><span data-stu-id="3e2ca-186">The registered address of the customer's company/organization.</span></span> <span data-ttu-id="3e2ca-187">Herhangi bir uzunluk sınırlaması hakkında bilgi için bkz. [Adres](utility-resources.md#address) kaynağı.</span><span class="sxs-lookup"><span data-stu-id="3e2ca-187">See the [Address](utility-resources.md#address) resource for information on any length limitations.</span></span>                                             |

#### <a name="company-profile"></a><span data-ttu-id="3e2ca-188">Şirket profili</span><span class="sxs-lookup"><span data-stu-id="3e2ca-188">Company profile</span></span>

<span data-ttu-id="3e2ca-189">Bu tabloda, yeni bir müşteri oluşturmak için gereken [Customercompanyprofile](customer-resources.md#customercompanyprofile) kaynağından gereken en düşük alan açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3e2ca-189">This table describes the minimum required fields from the [CustomerCompanyProfile](customer-resources.md#customercompanyprofile) resource needed to create a new customer.</span></span>

| <span data-ttu-id="3e2ca-190">Ad</span><span class="sxs-lookup"><span data-stu-id="3e2ca-190">Name</span></span>   | <span data-ttu-id="3e2ca-191">Tür</span><span class="sxs-lookup"><span data-stu-id="3e2ca-191">Type</span></span>   | <span data-ttu-id="3e2ca-192">Gerekli</span><span class="sxs-lookup"><span data-stu-id="3e2ca-192">Required</span></span> | <span data-ttu-id="3e2ca-193">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e2ca-193">Description</span></span>                                                  |
|--------|--------|----------|--------------------------------------------------------------|
| <span data-ttu-id="3e2ca-194">etki alanı</span><span class="sxs-lookup"><span data-stu-id="3e2ca-194">domain</span></span> | <span data-ttu-id="3e2ca-195">string</span><span class="sxs-lookup"><span data-stu-id="3e2ca-195">string</span></span> | <span data-ttu-id="3e2ca-196">Yes</span><span class="sxs-lookup"><span data-stu-id="3e2ca-196">Yes</span></span>     | <span data-ttu-id="3e2ca-197">Müşterinin etki alanı adı, örneğin contoso.onmicrosoft.com.</span><span class="sxs-lookup"><span data-stu-id="3e2ca-197">The customer's domain name, such as contoso.onmicrosoft.com.</span></span> |
| <span data-ttu-id="3e2ca-198">organizationRegistrationNumber</span><span class="sxs-lookup"><span data-stu-id="3e2ca-198">organizationRegistrationNumber</span></span> | <span data-ttu-id="3e2ca-199">string</span><span class="sxs-lookup"><span data-stu-id="3e2ca-199">string</span></span> | <span data-ttu-id="3e2ca-200">Koşula bağlıdır</span><span class="sxs-lookup"><span data-stu-id="3e2ca-200">Depends on condition</span></span> | <span data-ttu-id="3e2ca-201">Müşterinin kuruluş kayıt numarası (bazı ülkelerde ıNN numarası olarak da adlandırılır).</span><span class="sxs-lookup"><span data-stu-id="3e2ca-201">The customer’s organization registration number (also referred to as the INN number in certain countries).</span></span> <br/><br/><span data-ttu-id="3e2ca-202">Bu alanın tamamlanması yalnızca bir müşterinin şirketi/kuruluşu aşağıdaki ülkelerde bulunuyorsa gereklidir:</span><span class="sxs-lookup"><span data-stu-id="3e2ca-202">Completing this field is required only if a customer’s company/organization is located in the following countries:</span></span> <br/><br/><span data-ttu-id="3e2ca-203">-Ermenistan (Har)</span><span class="sxs-lookup"><span data-stu-id="3e2ca-203">- Armenia (AM)</span></span> <br/><span data-ttu-id="3e2ca-204">-Azerbaycan (AZ)</span><span class="sxs-lookup"><span data-stu-id="3e2ca-204">- Azerbaijan (AZ)</span></span><br/><span data-ttu-id="3e2ca-205">-Belarus (BY)</span><span class="sxs-lookup"><span data-stu-id="3e2ca-205">- Belarus (BY)</span></span><br/><span data-ttu-id="3e2ca-206">-Macaristan (HU)</span><span class="sxs-lookup"><span data-stu-id="3e2ca-206">- Hungary (HU)</span></span><br/><span data-ttu-id="3e2ca-207">-Kazakistan (KZ)</span><span class="sxs-lookup"><span data-stu-id="3e2ca-207">- Kazakhstan (KZ)</span></span><br/><span data-ttu-id="3e2ca-208">-Kırgızistan (KG)</span><span class="sxs-lookup"><span data-stu-id="3e2ca-208">- Kyrgyzstan (KG)</span></span><br/><span data-ttu-id="3e2ca-209">-Moldova (MD)</span><span class="sxs-lookup"><span data-stu-id="3e2ca-209">- Moldova (MD)</span></span><br/><span data-ttu-id="3e2ca-210">-Rusya (RU)</span><span class="sxs-lookup"><span data-stu-id="3e2ca-210">- Russia (RU)</span></span><br/><span data-ttu-id="3e2ca-211">-Tacikistan (TJ)</span><span class="sxs-lookup"><span data-stu-id="3e2ca-211">- Tajikistan (TJ)</span></span><br/><span data-ttu-id="3e2ca-212">-Özbekistan (UZ)</span><span class="sxs-lookup"><span data-stu-id="3e2ca-212">- Uzbekistan (UZ)</span></span><br/><span data-ttu-id="3e2ca-213">-Ukrayna (UA)</span><span class="sxs-lookup"><span data-stu-id="3e2ca-213">- Ukraine (UA)</span></span><br/><br/><span data-ttu-id="3e2ca-214">Müşterinin şirketi/kuruluşu burada gösterilenlerin ötesinde diğer ülkelerde bulunuyorsa bu alan gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="3e2ca-214">This field is not required if the customer’s company/organization is located in other countries beyond those shown here.</span></span>  |

### <a name="request-example"></a><span data-ttu-id="3e2ca-215">İstek örneği</span><span class="sxs-lookup"><span data-stu-id="3e2ca-215">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers HTTP/1.1
Authorization: Bearer <token>
MS-RequestId: d628adbe-b7ee-412e-ac55-58f22b4ba2f4
MS-CorrelationId: 0dd197a8-992c-44ca-aeae-21cd83494dce
X-Locale: en-US
MS-PartnerCenter-Client: Partner Center .NET SDK
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 823
Expect: 100-continue
Connection: Keep-Alive

{
    "Id": null,
    "CommerceId": null,
    "CompanyProfile": {
        "TenantId": null,
        "Domain": "WingtipToys678152504.onmicrosoft.com",
        "CompanyName": null,
        "Attributes": {
            "ObjectType": "CustomerCompanyProfile"
        }
    },
    "BillingProfile": {
        "Id": null,
        "FirstName": null,
        "LastName": null,
        "Email": "Gena@wingtiptoys.com",
        "Culture": "EN-US",
        "Language": "En",
        "CompanyName": "Wingtip Toys678152504",
        "DefaultAddress": {
            "Country": "US",
            "Region": null,
            "City": "Redmond",
            "State": "WA",
            "AddressLine1": "One Microsoft Way",
            "AddressLine2": null,
            "PostalCode": "98052",
            "FirstName": "Gena",
            "LastName": "Soto",
            "PhoneNumber": "4255550101"
        },
        "Attributes": {
            "ObjectType": "CustomerBillingProfile"
        }
    },
    "RelationshipToPartner": "none",
    "AllowDelegatedAccess": null,
    "UserCredentials": null,
    "CustomDomains": null,
    "AssociatedPartnerId": "484e548c-f5f3-4528-93a9-c16c6373cb59",
    "Attributes": {
        "ObjectType": "Customer"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="3e2ca-216">REST yanıtı</span><span class="sxs-lookup"><span data-stu-id="3e2ca-216">REST response</span></span>

<span data-ttu-id="3e2ca-217">Başarılı olursa, yanıt yeni müşteri için bir [Müşteri](customer-resources.md#customer) kaynağı içerir.</span><span class="sxs-lookup"><span data-stu-id="3e2ca-217">If successful, the response contains a [Customer](customer-resources.md#customer) resource for the new customer.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="3e2ca-218">Yanıt başarısı ve hata kodları</span><span class="sxs-lookup"><span data-stu-id="3e2ca-218">Response success and error codes</span></span>

<span data-ttu-id="3e2ca-219">Yanıtlar, başarı veya başarısızlık ve ek hata ayıklama bilgilerini gösteren bir HTTP durum kodu ile gelir.</span><span class="sxs-lookup"><span data-stu-id="3e2ca-219">Responses come with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="3e2ca-220">Bu kodu, hata türünü ve ek parametreleri okumak için bir ağ izleme aracı kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e2ca-220">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="3e2ca-221">Tam liste için bkz. [Iş ortağı MERKEZI Rest hata kodları](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="3e2ca-221">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="3e2ca-222">Yanıt örneği</span><span class="sxs-lookup"><span data-stu-id="3e2ca-222">Response example</span></span>

```http
HTTP/1.1 201 Created
Content-Length: 1085
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 0dd197a8-992c-44ca-aeae-21cd83494dce
MS-RequestId: d628adbe-b7ee-412e-ac55-58f22b4ba2f4
MS-CV: Yy/YaA0gYEmfQyR/.0
MS-ServerId: 030020525
Date: Tue, 06 Jun 2017 23:11:40 GMT

{
    "id": "626099fe-17af-4756-9fd0-6a73b7127859",
    "commerceId": "626099fe-17af-4756-9fd0-6a73b7127859",
    "companyProfile": {
        "tenantId": "626099fe-17af-4756-9fd0-6a73b7127859",
        "domain": "WingtipToys678152504.onmicrosoft.com",
        "companyName": "Wingtip Toys678152504",
        "links": {
            "self": {
                "uri": "/customers/626099fe-17af-4756-9fd0-6a73b7127859/profiles/company",
                "method": "GET",
                "headers": []
            }
        },
        "attributes": {
            "objectType": "CustomerCompanyProfile"
        }
    },
    "billingProfile": {
        "id": "7079246e-7b62-56ef-7cbd-a819514b54b5",
        "email": "Gena@wingtiptoys.com",
        "culture": "en-US",
        "language": "En",
        "companyName": "Wingtip Toys678152504",
        "defaultAddress": {
            "country": "US",
            "city": "Redmond",
            "state": "WA",
            "addressLine1": "One Microsoft Way",
            "postalCode": "98052",
            "firstName": "Gena",
            "lastName": "Soto",
            "phoneNumber": "4255550101"
        },
        "attributes": {
            "etag": "-8799889149591823008",
            "objectType": "CustomerBillingProfile"
        }
    },
    "relationshipToPartner": "reseller",
    "allowDelegatedAccess": true,
    "userCredentials": {
        "userName": "admin",
        "password": "0Krha*Io"
    },
    "associatedPartnerId": "484e548c-f5f3-4528-93a9-c16c6373cb59",
    "attributes": {
        "objectType": "Customer"
    }
}
```