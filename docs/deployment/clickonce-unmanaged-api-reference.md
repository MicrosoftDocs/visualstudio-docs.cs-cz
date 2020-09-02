---
title: Reference nespravovaného rozhraní API pro ClickOnce | Microsoft Docs
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
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 3b536a17df4f54158aa6f157a0d9795cf359ddc0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62900268"
---
# <a name="clickonce-unmanaged-api-reference"></a>Reference nespravovaného rozhraní API ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Nespravovaná veřejná rozhraní API z dfshim.dll.

## <a name="cleanonlineappcache"></a>CleanOnlineAppCache
 Vyčistí nebo odinstaluje všechny online aplikace z [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mezipaměti aplikace.

### <a name="return-value"></a>Vrácená hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí hodnotu HRESULT, která představuje chybu. Pokud dojde k spravované výjimce, vrátí 0x80020009 (DISP_E_EXCEPTION).

### <a name="remarks"></a>Poznámky
 Volání CleanOnlineAppCache spustí službu, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Pokud ještě není spuštěná.

## <a name="getdeploymentdatafrommanifest"></a>GetDeploymentDataFromManifest
 Načte informace o nasazení z manifestu a adresy URL aktivace.

### <a name="parameters"></a>Parametry

|Parametr|Popis|Typ|
|---------------|-----------------|----------|
|`pcwzActivationUrl`|Ukazatel na `ActivationURL` .|LPCWSTR|
|`pcwzPathToDeploymentManifest`|Ukazatel na `PathToDeploymentManifest` .|LPCWSTR|
|`pwzApplicationIdentity`|Ukazatel na vyrovnávací paměť, který získá řetězec zakončený hodnotou NULL, který určuje úplnou identitu aplikace vrácenou.|LPWSTR|
|`pdwIdentityBufferLength`|Ukazatel na DWORD, který je délkou `pwzApplicationIdentity` vyrovnávací paměti v WCHARs. To zahrnuje místo pro ukončovací znak NULL.|LPDWORD|
|`pwzProcessorArchitecture`|Ukazatel na vyrovnávací paměť pro příjem řetězce zakončeného hodnotou NULL, který určuje architekturu procesoru pro nasazení aplikace, z manifestu.|LPWSTR|
|`pdwArchitectureBufferLength`|Ukazatel na DWORD, který je délkou `pwzProcessorArchitecture` vyrovnávací paměti v WCHARs.|LPDWORD|
|`pwzApplicationManifestCodebase`|Ukazatel na vyrovnávací paměť pro příjem řetězce zakončeného hodnotou NULL, který určuje základ kódu manifestu aplikace, z manifestu.|LPWSTR|
|`pdwCodebaseBufferLength`|Ukazatel na DWORD, který je délkou `pwzApplicationManifestCodebase` vyrovnávací paměti v WCHARs.|LPDWORD|
|`pwzDeploymentProvider`|Ukazatel na vyrovnávací paměť pro příjem řetězce zakončeného hodnotou NULL, který určuje poskytovatele nasazení z manifestu, pokud je k dispozici. V opačném případě je vrácen prázdný řetězec.|LPWSTR|
|`pdwProviderBufferLength`|Ukazatel na DWORD, který je délkou `pwzProviderBufferLength` .|LPDWORD|

### <a name="return-value"></a>Vrácená hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí hodnotu HRESULT, která představuje chybu. Vrátí HRESULTFROMWIN32 (ERROR_INSUFFICIENT_BUFFER), pokud je vyrovnávací paměť příliš malá.

### <a name="remarks"></a>Poznámky
 Ukazatele nesmí mít hodnotu null. `pcwzActivationUrl` a `pcwzPathToDeploymentManifest` nesmí být prázdný.

 Je zodpovědností volajícího vyčistit adresu URL aktivace. Například přidávání řídicích znaků tam, kde jsou potřeba, nebo odebrání řetězce dotazu.

 Je zodpovědností volajícího omezit délku vstupu. Například maximální délka adresy URL je 2 KB.

## <a name="launchapplication"></a>LaunchApplication
 Spustí nebo nainstaluje aplikaci pomocí adresy URL nasazení.

### <a name="parameters"></a>Parametry

|Parametr|Popis|Typ|
|---------------|-----------------|----------|
|`deploymentUrl`|Ukazatel na řetězec zakončený hodnotou NULL, který obsahuje adresu URL manifestu nasazení.|LPCWSTR|
|`data`|Vyhrazeno pro budoucí použití. Musí mít hodnotu NULL.|LPVOID|
|`flags`|Vyhrazeno pro budoucí použití. Musí mít hodnotu 0.|DWORD|

### <a name="return-value"></a>Vrácená hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí hodnotu HRESULT, která představuje chybu. Pokud dojde k spravované výjimce, vrátí 0x80020009 (DISP_E_EXCEPTION).

## <a name="see-also"></a>Viz také
- <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>