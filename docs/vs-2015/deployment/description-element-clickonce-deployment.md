---
title: '&lt;Popis&gt; – Element (nasazení ClickOnce) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: wpickett
ms.openlocfilehash: 8ddba6356ab051dbad27e55eefd53a517b47a21a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49224767"
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;Popis&gt; – Element (nasazení ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Určuje informace o aplikaci použít k vytvoření prostředí prezentace a **přidat nebo odebrat programy** v Ovládacích panelech.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      <description   
   publisher   
   product  
   suiteName  
   supportUrl  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementy a atributy  
 `description` Element je povinný a je v `urn:schemas-microsoft-com:asm.v1` oboru názvů. Neobsahuje žádné podřízené prvky a má následující atributy.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`publisher`|Požadováno. Určuje název společnosti použít pro umístění ikony v Windows **Start** nabídky a **přidat nebo odebrat programy** v Ovládacích panelech, když je nasazení nakonfigurováno pro instalaci.|  
|`product`|Požadováno. Určuje úplný název produktu. Použít jako název ikona nainstalované v Windows **Start** nabídky.|  
|`suiteName`|Volitelné. Identifikuje podsložku v rámci `publisher` složky v Windows **Start** nabídky.|  
|`supportUrl`|Volitelné. Určuje adresu URL podpory, který je zobrazen v **přidat nebo odebrat programy** v Ovládacích panelech. Je také vytvořen zástupce na tuto adresu URL pro podporu aplikace v Windows **Start** nabídky, pokud je nasazení nakonfigurováno pro instalaci.|  
  
## <a name="remarks"></a>Poznámky  
 Ve všech konfiguracích nasazení je vyžadován popis prvek.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje `description` prvek [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestu nasazení. Tento příklad kódu je součástí většího příkladu určeného pro [Manifest nasazení ClickOnce](../deployment/clickonce-deployment-manifest.md) tématu.  
  
```  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>Viz také  
 [ClickOnce – manifest nasazení](../deployment/clickonce-deployment-manifest.md)



