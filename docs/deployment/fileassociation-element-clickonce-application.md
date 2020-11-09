---
title: '&lt;Element Association &gt; (aplikace ClickOnce) | Microsoft Docs'
description: Element Association identifikuje příponu souboru, která se má přidružit k aplikaci. Element Association je nepovinný.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <fileAssociation> element [ClickOnce application manifest]
- manifests [ClickOnce], fileAssociation element
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f1908b4f63edcf90643c28523c0c6ed0d0e11a97
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382725"
---
# <a name="ltfileassociationgt-element-clickonce-application"></a>&lt;element Association &gt; (aplikace ClickOnce)
Určuje příponu souboru, která má být přidružena k aplikaci.

## <a name="syntax"></a>Syntax

```xml
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

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nebude přepisovat existující přidružení souborů. Aplikace ClickOnce však může přepsat příponu souboru pouze pro aktuálního uživatele. Po odinstalaci aplikace ClickOnce odstraní ClickOnce přidružení souboru pro uživatele a přidružení vázané na počítač bude opět aktivní.

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje `fileAssociation` prvky v manifestu aplikace pro aplikaci textový editor nasazené pomocí [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Tento příklad kódu také obsahuje [ \<file> element](../deployment/file-element-clickonce-application.md) vyžadovaný `defaultIcon` atributem.

```xml
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
- [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md)