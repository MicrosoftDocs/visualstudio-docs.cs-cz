---
title: 'Postupy: vytvoření schématu XML z dokumentu XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 59e99320b122424e40da64b530bfe9a84a93eae1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670932"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Postupy: Vytvoření schématu XML z dokumentu XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editor XML umožňuje vytvořit schéma XML schématu definice jazyka (XSD) z dokumentu XML. Dokument instance XML určuje, jak je schéma generováno následujícím způsobem:

- Pokud k dokumentu XML není k dispozici žádné schéma nebo definice typu dokumentu (DTD), data v dokumentu XML slouží k odvození nového schématu XML.

- Pokud dokument XML obsahuje přidruženou DTD, je externí deklarace DTD a vnitřní podmnožina převedena na odpovídající schéma XML.

- Pokud dokument XML obsahuje vložené schéma se sníženými daty XML (XDR), schéma XDR je převedeno na odpovídající schéma XML.

  Vytvořená schémata se pak použijí k poskytnutí IntelliSense pro dokument XML.

  Další informace o modulu odvození schématu naleznete v tématu [odvození schématu XML](https://msdn.microsoft.com/library/b18e7ffd-3c04-482d-9934-ba2f6a59b2c9).

### <a name="to-create-an-xml-schema"></a>Vytvoření schématu XML

1. Načte dokument instance XML do editoru XML.

2. Klikněte na tlačítko **vytvořit schéma** z **panelu nástrojů**.

     Dokument schématu XML je vytvořen a otevřen pro každý obor názvů nalezený v dokumentu instance XML. Každé schéma je otevřeno jako dočasný různé soubory.

     Schémata lze uložit na disk, přidat do projektu nebo zahodit.

    > [!NOTE]
    > Příkaz **vytvořit schéma** je také k dispozici v místní nabídce editoru XML a v nabídce **XML** .

## <a name="see-also"></a>Viz také
 [Editor XML](../xml-tools/xml-editor.md)
