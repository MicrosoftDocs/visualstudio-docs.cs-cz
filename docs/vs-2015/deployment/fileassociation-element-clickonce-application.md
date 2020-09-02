---
title: '&lt;Element Association &gt; (aplikace ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <fileAssociation> element [ClickOnce application manifest]
- manifests [ClickOnce], fileAssociation element
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4b31ac34627b244cb61b6fdb5c6ca214675ec045
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150846"
---
# <a name="ltfileassociationgt-element-clickonce-application"></a>&lt;Element Association &gt; (aplikace ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Určuje příponu souboru, která má být přidružena k aplikaci.  
  
## <a name="syntax"></a>Syntax  
  
```  
<fileAssociation  
    xmlns="urn:schemas-microsoft-com:clickonce.v1"  
    extension  
    description  
    progid  
    defaultIcon  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementy a atributy  
 `fileAssociation`Element je nepovinný. Element má následující atributy.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`extension`|Povinná hodnota. Přípona souboru, která má být přidružena k aplikaci.|  
|`description`|Povinná hodnota. Popis typu souboru pro použití prostředím|  
|`progid`|Povinná hodnota. Název, který jednoznačně identifikuje typ souboru.|  
|`defaultIcon`|Povinná hodnota. Určuje ikonu, která se má použít pro soubory s tímto rozšířením. Soubor ikony musí být zadán pomocí [ \<file> elementu](../deployment/file-element-clickonce-application.md) v rámci [ \<assembly> elementu](../deployment/assembly-element-clickonce-application.md) , který obsahuje tento element.|  
  
## <a name="remarks"></a>Poznámky  
 Tento prvek musí zahrnovat odkaz na obor názvů XML na "urn: schemas-microsoft-com: ClickOnce. v1". Pokud `<fileAssociation>` je element použit, musí být za `<application>` prvkem v jeho nadřazeném [ \<assembly> elementu](../deployment/assembly-element-clickonce-application.md).  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nebude přepisovat existující přidružení souborů. Aplikace ClickOnce však může přepsat příponu souboru pouze pro aktuálního uživatele. Po odinstalaci aplikace ClickOnce odstraní ClickOnce přidružení souboru pro uživatele a přidružení vázané na počítač bude opět aktivní.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje `fileAssociation` prvky v manifestu aplikace pro aplikaci textový editor nasazené pomocí [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Tento příklad kódu také obsahuje [ \<file> element](../deployment/file-element-clickonce-application.md) vyžadovaný `defaultIcon` atributem.  
  
```  
<file name="text.ico" size="4286">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>0joAqhmfeBb93ZneZv/oTMP2brY=</dsig:DigestValue>  
  </hash>  
</file>  
<file name="writing.ico" size="9662">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>2cL2U7cm13nG40v9MQdxYKazIwI=</dsig:DigestValue>  
  </hash>  
</file>  
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".text" description="Text  Document (ClickOnce)" progid="Text.Document" defaultIcon="text.ico" />  
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".writing" description="Writings (ClickOnce)" progid="Writing.Document" defaultIcon="writing.ico" />  
```  
  
## <a name="see-also"></a>Viz také  
 [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md)
