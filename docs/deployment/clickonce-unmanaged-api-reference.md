---
title: ClickOnce – nespravované rozhraní API | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
api_name:
- CleanOnlineAppCache
- GetDeploymentDataFromManifest
- LaunchApplication
api_location:
- dfshim.dll
api_type:
- COM
topic_type:
- apiref
ms.technology: vs-ide-deployment
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- LaunchApplication [ClickOnce unmanaged]
- ClickOnce, unmanaged APIs
- CleanOnlineAppCache [ClickOnce unmanaged]
- CleanOnlineAppCacheW interface [ClickOnce unmanaged]
- GetDeploymentDataFromManifest [ClickOnce unmanaged]
ms.assetid: ec002138-4054-456d-bcc1-79ac2f4a4fd7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 121b9b3be3c7f942f3ed1d5f7f2600f24d684e2d
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2018
ms.locfileid: "39082160"
---
# <a name="clickonce-unmanaged-api-reference"></a>ClickOnce – nespravované rozhraní API
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nespravované veřejného rozhraní API z dfshim.dll.  
  
## <a name="cleanonlineappcache"></a>CleanOnlineAppCache zapne  
 Čistí nebo odinstaluje všechny aplikace, které jsou z online [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mezipaměti aplikace.  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí hodnotu S_OK; jinak vrátí hodnotu, která představuje chybu HRESULT. Pokud dojde k spravované výjimky, vrátí 0x80020009 (DISP_E_EXCEPTION).  
  
### <a name="remarks"></a>Poznámky  
 Volání CleanOnlineAppCache zapne [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] služby, pokud ještě není spuštěná.  
  
## <a name="getdeploymentdatafrommanifest"></a>GetDeploymentDataFromManifest  
 Načte informace o nasazení z manifestu a aktivace adresy URL.  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|Typ|  
|---------------|-----------------|----------|  
|`pcwzActivationUrl`|Ukazatel `ActivationURL`.|LPCWSTR|  
|`pcwzPathToDeploymentManifest`|Ukazatel `PathToDeploymentManifest`.|LPCWSTR|  
|`pwzApplicationIdentity`|Ukazatel do vyrovnávací paměti pro příjem řetězec zakončený hodnotou NULL, který určuje, vrátí identitu celou aplikaci.|LPWSTR|  
|`pdwIdentityBufferLength`|Ukazatel na DWORD, který je délka `pwzApplicationIdentity` v WCHARs vyrovnávací paměti. Zahrnuje to prostor pro ukončovací znak NULL.|LPDWORD|  
|`pwzProcessorArchitecture`|Ukazatel do vyrovnávací paměti pro příjem řetězec zakončený hodnotou NULL, který určuje architekturu procesoru nasazení aplikace z manifestu.|LPWSTR|  
|`pdwArchitectureBufferLength`|Ukazatel na DWORD, který je délka `pwzProcessorArchitecture` v WCHARs vyrovnávací paměti.|LPDWORD|  
|`pwzApplicationManifestCodebase`|Ukazatel do vyrovnávací paměti pro příjem řetězec zakončený hodnotou NULL, který určuje základ kódu manifestu aplikace z manifestu.|LPWSTR|  
|`pdwCodebaseBufferLength`|Ukazatel na DWORD, který je délka `pwzApplicationManifestCodebase` v WCHARs vyrovnávací paměti.|LPDWORD|  
|`pwzDeploymentProvider`|Ukazatel do vyrovnávací paměti pro příjem řetězec zakončený hodnotou NULL, která určuje, poskytovatele nasazení z manifestu, pokud jsou k dispozici. V opačném případě je vrácen prázdný řetězec.|LPWSTR|  
|`pdwProviderBufferLength`|Ukazatel na DWORD, který je délka `pwzProviderBufferLength`.|LPDWORD|  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí hodnotu S_OK; jinak vrátí hodnotu, která představuje chybu HRESULT. Vrátí HRESULTFROMWIN32(ERROR_INSUFFICIENT_BUFFER), pokud vyrovnávací paměť je příliš malá.  
  
### <a name="remarks"></a>Poznámky  
 Ukazatele nesmí mít hodnotu null. `pcwzActivationUrl` a `pcwzPathToDeploymentManifest` nesmí být prázdný.  
  
 Je odpovědností volajícího k vyčištění aktivační adrese URL. Například přidání řídicích znaků, kde jsou potřeba nebo odebrání řetězce dotazu.  
  
 Je odpovědností volajícího a omezit délku vstupu. Maximální délka adresy URL je například 2KB.  
  
## <a name="launchapplication"></a>LaunchApplication  
 Spustí nebo instaluje aplikace pomocí adresy URL nasazení.  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|Typ|  
|---------------|-----------------|----------|  
|`deploymentUrl`|Ukazatel na řetězec zakončený hodnotou NULL, který obsahuje adresu URL v manifestu nasazení.|LPCWSTR|  
|`data`|Vyhrazeno pro budoucí použití. Musí mít hodnotu NULL.|LPVOID –|  
|`flags`|Vyhrazeno pro budoucí použití. Musí být 0.|DWORD|  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí hodnotu S_OK; jinak vrátí hodnotu, která představuje chybu HRESULT. Pokud dojde k spravované výjimky, vrátí 0x80020009 (DISP_E_EXCEPTION).  
  
## <a name="see-also"></a>Viz také:  
 <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>