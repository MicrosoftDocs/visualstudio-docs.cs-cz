---
title: Vytvoření schématu XML
description: Naučte se používat editor XML v aplikaci Visual Studio k vytvoření schématu XML Schema Definition Language (XSD) z dokumentu XML.
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: how-to
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e33a4add7ebc6a3e323331731f3183d7a0dce26f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970280"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Postupy: vytvoření schématu XML z dokumentu XML

Editor XML umožňuje vytvořit schéma XML Schema Definition Language (XSD) z dokumentu XML. Soubor XML určuje, jak je schéma generováno následujícím způsobem:

- Pokud k dokumentu XML není k dispozici žádné schéma nebo definice typu dokumentu (DTD), data v dokumentu XML slouží k odvození nového schématu XML.

- Pokud dokument XML obsahuje přidruženou DTD, je externí deklarace DTD a vnitřní podmnožina převedena na odpovídající schéma XML.

- Pokud dokument XML obsahuje vložené schéma XML-Data zmenšeno (XDR), schéma XDR je převedeno na odpovídající schéma XML.

Vytvořená schémata jsou pak použita k poskytnutí IntelliSense pro soubor XML.

Další informace o modulu odvození schématu naleznete v tématu [odvození schématu XML](/dotnet/standard/data/xml/inferring-an-xml-schema).

## <a name="to-create-an-xml-schema"></a>Vytvoření schématu XML

1. Otevřete soubor XML v aplikaci Visual Studio.

2. Na panelu nabídek vyberte **XML**  >  **vytvořit schéma**.

   Dokument schématu XML je vytvořen a otevřen pro každý obor názvů nalezený v souboru XML. Každé schéma je otevřeno jako dočasný různé soubory. Schémata lze uložit na disk, přidat do projektu nebo zahodit.

## <a name="see-also"></a>Viz také

- [Editor XML](../xml-tools/xml-editor.md)
