---
title: 'Postup: Vytvoření informačního kanálu Atom pro soukromou galerii | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c72fbf2d3973ffd84de1cf6f33788c43511c3ce4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711010"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Postup: Vytvoření informačního kanálu Atom pro soukromou galerii
Můžete vytvořit informační kanál Atom (RSS) do umístění v intranetu, který obsahuje rozšíření, a přidat informační kanál do **rozšíření a aktualizací** jako soukromou galerii. Další informace naleznete v [tématu Soukromé galerie](../extensibility/private-galleries.md).

## <a name="create-an-atom-feed"></a>Vytvoření informačního kanálu Atom
 Chcete-li vytvořit informační kanál Atom jako soukromou galerii, nejprve shromážděte rozšíření *(soubory všest)* do složky. Pokud chcete, můžete je uspořádat do podsložek. Budete také potřebovat následující zdroje:

- Soubor *atom.xml,* který zpřístupňuje přípony jako soukromou galerii. Informace o připojení souboru *atom.xml* k **rozšířením a aktualizacím**naleznete [v tématu Soukromé galerie](../extensibility/private-galleries.md).

- Složka obsahující všechny obrazové soubory, které byly extrahovány z rozšíření (například snímky obrazovek). Soubor *atom.xml* obsahuje relativní odkazy na tyto obrázky tak, aby byly k dispozici v **rozšíření a aktualizace**.

  Předpokládejme například, že jste shromáždili následující dvě rozšíření do složky:

- *Template_Wizard_239.vsix*, což je prázdná šablona projektu VSIX.

- *SelectionHighlight.vsix*, což je nástroj pro zvýraznění všech instancí vybraného slova.

  Obsah souboru *atom.xml* by se podobal následujícímu příkladu:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<feed xmlns="http://www.w3.org/2005/Atom">
  <title type="text" />
  <id>uuid:bcecded5-97c8-4d24-96f1-7d9e16652433;id=1</id>
  <updated>2011-04-14T21:25:48Z</updated>
  <entry>
    <id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</id>
    <title type="text">Highlight all occurrences of selected word</title>
    <summary type="text">This extends the editor to highlight ....</summary>
    <published>2011-04-14T14:24:51-07:00</published>
    <updated>2011-04-14T14:24:22-07:00</updated>
    <author>
      <name>Microsoft</name>
    </author>
    <link rel="icon" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_Icon_SelectionHighlightIcon.jpg" />
    <link rel="previewimage" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_PreviewImage_SelectionHighlight.jpg" />
    <content type="application/octet-stream" src="SelectionHighlight.vsix" />
    <Vsix xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
      <Id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</Id>
      <Version>1.31</Version>
      <References />
      <Rating xsi:nil="true" />
      <RatingCount xsi:nil="true" />
      <DownloadCount xsi:nil="true" />
    </Vsix>
  </entry>
  <entry>
    <id>Template_Wizard_239.Microsoft.3b38a7e3-5cbc-4389-a92a-d82tyc2ed592</id>
    ...
  </entry>
</feed>
```

 Všimněte si, že dvě značky odkazů odkazují na snímky obrazovek v generované složce obrázků.

## <a name="see-also"></a>Viz také
- [Soukromé galerie](../extensibility/private-galleries.md)
