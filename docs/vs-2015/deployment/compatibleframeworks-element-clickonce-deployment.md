---
title: '&lt;compatibleFrameworks – &gt; element (nasazení ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <compatibleFrameworks> element [ClickOnce deployment manifest]
ms.assetid: f6c3ee55-9e65-403d-8664-3ebde872c7d4
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ef54062bd74c9395e187503dd12db1c0cd70d822
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675418"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;compatibleFrameworks – &gt; element (nasazení ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identifikuje verze .NET Framework, kde se tato aplikace může nainstalovat a spustit.  
  
> [!NOTE]
> [MageUI.exe](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14) nepodporuje `compatibleFrameworks` element při ukládání manifestu aplikace, který již byl podepsán pomocí certifikátu pomocí [MageUI.exe](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14). Místo toho je nutné použít [Mage.exe](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1).  
  
## <a name="syntax"></a>Syntax  
  
```  
<compatibleFrameworks  
      SupportUrl>   
   <framework  
      targetVersion  
      profile  
      supportedRuntime  
   />   
</ compatibleFrameworks>  
```  
  
## <a name="elements-and-attributes"></a>Elementy a atributy  
 `compatibleFrameworks`Element je vyžadován pro manifesty nasazení, které cílí na [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] modul runtime, který poskytuje [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] nebo později. `compatibleFrameworks`Element obsahuje jeden nebo více `framework` prvků, které určují .NET Framework verze, na kterých lze tuto aplikaci spustit. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Modul runtime spustí aplikaci na první dostupné `framework` v tomto seznamu.  
  
 V následující tabulce je uveden atribut, který `compatibleFrameworks` podporuje element.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`S` `upportUrl`|Nepovinný parametr. Určuje adresu URL, kam lze stáhnout upřednostňovanou kompatibilní verzi .NET Framework.|  
  
## <a name="framework"></a>rozhraní  
 Povinná hodnota. V následující tabulce jsou uvedeny atributy, které `framework` prvek podporuje.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`targetVersion`|Povinná hodnota. Určuje číslo verze cílového .NET Framework.|  
|`profile`|Povinná hodnota. Určuje profil cílového .NET Framework.|  
|`supportedRuntime`|Povinná hodnota. Určuje číslo verze modulu runtime přidruženého k cílovému .NET Framework.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje `compatibleFrameworks` prvek v [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestu nasazení. Toto nasazení může běžet na [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] . Může také běžet na, [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] protože je nadmnožinou [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] .  
  
```  
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">  
  <framework   
      targetVersion="4.0"   
      profile="Client"   
      supportedRuntime="4.0.30319" />  
</compatibleFrameworks>  
```  
  
## <a name="see-also"></a>Viz také  
 [ClickOnce – manifest nasazení](../deployment/clickonce-deployment-manifest.md)
