---
title: '&lt;Description – &gt; element (nasazení ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#description
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <description> element [ClickOnce deployment manifest]
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cadf4a0b525e5603247748edd63516dc26d8a0b6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187750"
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;Description – &gt; element (nasazení ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identifikuje informace o aplikaci používané k vytvoření stavu prostředí a položky **Přidat nebo odebrat programy** v Ovládacích panelech.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      <description   
   publisher   
   product  
   suiteName  
   supportUrl  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementy a atributy  
 `description`Element je povinný a je v `urn:schemas-microsoft-com:asm.v1` oboru názvů. Neobsahuje žádné podřízené elementy a má následující atributy.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`publisher`|Povinná hodnota. Určuje název společnosti, který se používá pro umístění ikon v nabídce **Start** systému Windows a položka **Přidat nebo odebrat programy** v Ovládacích panelech, pokud je nasazení nakonfigurováno pro instalaci.|  
|`product`|Povinná hodnota. Určuje úplný název produktu. Používá se jako název ikony nainstalované v nabídce **Start** systému Windows.|  
|`suiteName`|Nepovinný parametr. Identifikuje podsložku v rámci `publisher` složky v nabídce **Start** systému Windows.|  
|`supportUrl`|Nepovinný parametr. Určuje adresu URL podpory, která se zobrazí v položce **Přidat nebo odebrat programy** v Ovládacích panelech. Zástupce této adresy URL je vytvořen také pro podporu aplikací v nabídce **Start** systému Windows, pokud je nasazení nakonfigurováno pro instalaci.|  
  
## <a name="remarks"></a>Poznámky  
 Element Description je vyžadován ve všech konfiguracích nasazení.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje `description` prvek v [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestu nasazení. Tento příklad kódu je součástí většího příkladu, který je k dispozici v tématu [manifestu nasazení ClickOnce](../deployment/clickonce-deployment-manifest.md) .  
  
```  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>Viz také  
 [ClickOnce – manifest nasazení](../deployment/clickonce-deployment-manifest.md)
