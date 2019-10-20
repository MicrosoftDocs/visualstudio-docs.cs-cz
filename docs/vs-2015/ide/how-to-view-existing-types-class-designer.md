---
title: 'Postupy: zobrazení existujících typů (Návrhář tříd) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.CannotShowBaseType
helpviewer_keywords:
- types [Visual Studio], visualizing
- types [Visual Studio], class diagrams
- class diagrams, types
ms.assetid: de110a4e-5b51-4a40-9dee-615df4d8f999
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 925220d583695e0116fb5901d92626bfcfa7450f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670546"
---
# <a name="how-to-view-existing-types-class-designer"></a>Postupy: Zobrazení existujících typů (návrhář tříd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chcete-li zobrazit existující typ a jeho členy, přidejte její tvar do diagramu tříd.

 Můžete vidět místní a odkazované typy. V aktuálně otevřeném projektu existuje místní typ a je pro čtení i zápis. Odkazovaný typ existuje v jiném projektu nebo v odkazovaném sestavení a je jen pro čtení.

 Chcete-li navrhnout nové typy v diagramech tříd, přečtěte si téma [Postupy: vytváření typů pomocí Návrhář tříd](../ide/how-to-create-types-by-using-class-designer.md).

### <a name="to-see-types-in-a-project-on-a-class-diagram"></a>Zobrazení typů v projektu v diagramu tříd

1. Z projektu v okně Průzkumník řešení otevřete existující soubor diagramu tříd (.cd). Nebo pokud neexistuje žádný diagram tříd, přidejte do projektu nový diagram tříd. Viz [Postupy: Přidání diagramů tříd do projektů (návrhář tříd)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).

2. Z okna Průzkumník řešení přetáhněte soubor zdrojového kódu do diagramu tříd.

   > [!WARNING]
   > Pokud má vaše řešení projekt, který sdílí kód napříč více aplikacemi, můžete přetáhnout soubory nebo kód do diagramu tříd pouze z těchto zdrojů:
   >
   > - Projekt aplikace, který obsahuje diagram
   >   - Sdílený projekt, který byl importován projektem aplikace
   >   - Odkazovaný projekt
   >   - Sestavení

    Tvary, které představují typy definované v souboru zdrojového kódu, se zobrazí v diagramu na pozici, kam jste soubor přetáhli.

   V projektu lze také zobrazit typy přetažením jednoho nebo více typů z uzlu projektu v zobrazení tříd do diagramu tříd.

> [!TIP]
> Pokud Zobrazení tříd není otevřený, otevřete Zobrazení tříd v nabídce **zobrazení** . Další informace o Zobrazení tříd naleznete v tématu [zobrazení tříd a jejich členů](https://msdn.microsoft.com/71e9e8f3-261a-4e0c-87bf-5ec48b8bf333).

 Chcete-li zobrazit typy ve výchozích umístěních v diagramu, vyberte jeden nebo více typů v Zobrazení tříd, klikněte pravým tlačítkem myši na vybrané typy a zvolte možnost **Zobrazit diagram tříd**.

> [!NOTE]
> Pokud v projektu existuje zavřený diagram tříd obsahující daný typ, diagram tříd se otevře a zobrazí tvar typu. Pokud ale v projektu neexistuje žádný diagram tříd obsahující daný typ, Návrhář tříd vytvoří v projektu nový diagram tříd a otevře jej pro zobrazení typu.

 Při prvním zobrazení typu v diagramu se jeho tvar ve výchozím nastavení zobrazí sbalený. Tvar můžete rozbalit a zobrazit jeho obsah.

### <a name="to-display-the-contents-of-a-project-in-a-class-diagram"></a>Zobrazení obsahu projektu v diagramu tříd

1. V Průzkumník řešení nebo Zobrazení tříd klikněte pravým tlačítkem myši na projekt a zvolte možnost **Zobrazit**a pak zvolte možnost **Zobrazit diagram tříd**.

     Vytvoří se automaticky vyplněný diagram tříd.

## <a name="see-also"></a>Viz také
 [Postupy: zobrazení dědičnosti mezi typy (návrhář tříd)](../ide/how-to-view-inheritance-between-types-class-designer.md) [Postupy: přizpůsobení diagramů tříd (návrhář tříd)](../ide/how-to-customize-class-diagrams-class-designer.md) [zobrazení typů a vztahů (návrhář tříd)](../ide/viewing-types-and-relationships-class-designer.md)
