---
title: Dialogové okno Upřesnit nastavení kompilátoru (Visual Basic)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAdvancedCompile
helpviewer_keywords:
- Advanced Compiler Settings dialog box
ms.assetid: 1f81133a-293f-4dba-bc1c-8baafb01d857
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 593bb95e45ecdbda14eba49425ce5db08369e6cf
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38783685"
---
# <a name="advanced-compiler-settings-dialog-box-visual-basic"></a>Dialogové okno Upřesnit nastavení kompilátoru (Visual Basic)

Použití **AdvancedCompiler nastavení** dialogovému oknu **Návrháře projektu** k určení rozšířenou vlastností konfigurace sestavení projektu. Toto dialogové okno se vztahují na projekty Visual Basic pouze.

## <a name="to-access-this-dialog-box"></a>Pro přístup k tomuto dialogovému oknu

1.  V **Průzkumníka řešení**, zvolte uzel projektu (ne **řešení** uzlu).

2.  Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. Když **Návrhář projektu** se zobrazí, klikněte na tlačítko **kompilace** kartu.

3.  Na [stránka kompilovat, Návrhář projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md), vyberte **konfigurace** a **platformy**. Ve zjednodušených konfigurací sestavení **konfigurace** a **platformy** seznamy se nezobrazují. Další informace najdete v tématu [postupy: nastavení ladění a vydání konfigurace](../../debugger/how-to-set-debug-and-release-configurations.md).

4.  Klikněte na tlačítko **Upřesnit možnosti kompilace**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="optimizations"></a>Optimalizace

 Určete následující možnosti optimalizace, které můžete v některých případech zmenšit soubor programu, programu pracovat rychleji a urychlit proces sestavení.

**Odebrat kontroly přetečení celých čísel**

Toto políčko zaškrtnuto, ve výchozím nastavení, povolíte kontrolu přetečení celého čísla. Zaškrtněte toto políčko, chcete-li odebrat kontroly přetečení celého čísla. Pokud toto políčko zaškrtnete, může být rychlejší výpočty celé číslo. Pokud odeberete přetečení kontrolu a datový typ kapacity přetečení, nesprávné výsledky může ukládat bez vyvolání chyby.

Pokud přetečení podmínky jsou kontrolovány a přetečení celočíselné operace <xref:System.OverflowException> je vyvolána výjimka. V případě přetečení podmínky nejsou zaškrtnuté, není operace přetečení celého čísla vyvolat výjimku.

**Povolit optimalizace**

Toto políčko zaškrtnuto, ve výchozím nastavení, chcete-li zakázat optimalizace kompilátoru. Výběr tohoto políčka povolíte optimalizace kompilátoru. Optimalizace kompilátoru zkontrolujte výstupní soubor menší, rychlejší a efektivnější. Nicméně protože optimalizace způsobit změnou kódu do výstupního souboru, optimalizace kompilátoru mohou ztížit ladění.

 **Základní adresa knihovny DLL**

 Toto textové pole se zobrazí výchozí základní adresa knihovny DLL v šestnáctkovém formátu. V projektech knihovny tříd a Knihovna ovládacích prvků vám pomůže tohoto textového pole zadejte základní adresu, která se dá použít při vytvoření knihovny DLL.

 **Generovat ladicí informace**

 Vyberte **žádný**, **úplné**, nebo **pouze soubor pdb** ze seznamu. **Žádný** Určuje, že nebudou generována žádná informace o ladění. **Úplné** Určuje, že nebudou generována úplné ladicí informace, a **pouze soubor pdb** Určuje, že by měly být generovány pouze soubor PDB ladicí informace. Výchozí hodnota pro tuto možnost je **úplné**.

## <a name="compilation-constants"></a>Kompilace konstanty

Konstanty pro podmíněnou kompilaci mít podobný pomocí vliv [#Const](/dotnet/visual-basic/language-reference/directives/const-directive) direktivy preprocesoru ve zdroji souborů, s tím rozdílem, že konstanty definované jsou veřejné a použít na všechny soubory v projektu. Můžete použít konstanty pro podmíněnou kompilaci spolu s [#If... Pak... #Else](/dotnet/visual-basic/language-reference/directives/if-then-else-directives) direktivy podmíněné kompilace zdrojové soubory. Zobrazit [podmíněné kompilace](/dotnet/visual-basic/programming-guide/program-structure/conditional-compilation).

 **Definovat konstantu DEBUG**

 Ve výchozím nastavení je toto políčko zaškrtnuto, určení nastavit konstantu DEBUG.

 **Definovat konstantu TRACE**

 Ve výchozím nastavení je toto políčko zaškrtnuto, určení nastavit konstantu TRACE.

 **Vlastní konstanty**

 Zadejte všechny vlastní konstanty pro vaši aplikaci do tohoto textového pole. Položky by měly být odděleny čárkami, pomocí tohoto formuláře: **Name1 = "Hodnota1", NAZEV2 = "Hodnota2", nazev3 = "Hodnota3"**.

## <a name="other-settings"></a>Další nastavení

**Generování sestavení serializace**

Toto nastavení určuje, zda kompilátor vytvoří sestavení serializace XML. Sestavení serializace mohou zvýšit výkon při spuštění <xref:System.Xml.Serialization.XmlSerializer> Pokud jste použili třídy k serializaci typů ve vašem kódu. Výchozí hodnota pro tuto možnost je **automaticky**. **Automatické** Určuje, že se serializace sestavení vytvoří pouze v případě, že jste použili <xref:System.Xml.Serialization.XmlSerializer> ke kódování typů ve vašem kódu pro XML. **Vypnout** Určuje, že sestavení serializace nebudou nikdy generována, bez ohledu na to, jestli váš kód používá <xref:System.Xml.Serialization.XmlSerializer>. **Na** Určuje, že sestavení serializace budou vždy generována. Jsou pojmenované sestavení serializace `TypeName`. XmlSerializers.dll.

## <a name="see-also"></a>Viz také:

- [Stránka Kompilovat, Návrhář projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)