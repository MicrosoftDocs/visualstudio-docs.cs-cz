---
title: Dialogové okno Upřesnit nastavení kompilátoru (Visual Basic)
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAdvancedCompile
helpviewer_keywords:
- Advanced Compiler Settings dialog box
ms.assetid: 1f81133a-293f-4dba-bc1c-8baafb01d857
author: TerryGLee
ms.author: ghogen
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 0c0e6e9d41bb1d4bd7446bb77306ca5a4551906f
ms.sourcegitcommit: 9e15138a34532b222e80f6b42b1a9de7b2fe0175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2020
ms.locfileid: "85419104"
---
# <a name="advanced-compiler-settings-dialog-box-visual-basic"></a>Dialogové okno Upřesnit nastavení kompilátoru (Visual Basic)

Pomocí dialogového okna **Nastavení AdvancedCompiler** **Návrháře projektu** můžete zadat rozšířené vlastnosti konfigurace sestavení projektu. Toto dialogové okno se vztahuje pouze na Visual Basic projekty.

## <a name="to-access-this-dialog-box"></a>Přístup k tomuto dialogovému oknu

1. V **Průzkumník řešení**vyberte uzel projektu (ne uzel **řešení** ).

2. V nabídce **projekt** klikněte na příkaz **vlastnosti**. Když se zobrazí **Návrhář projektu** , klikněte na kartu **kompilovat** .

3. Na [stránce kompilovat Návrháře projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)vyberte **konfiguraci** a **platformu**. Ve zjednodušených konfiguracích sestavení se nezobrazí seznamy **konfigurací** a **platforem** . Další informace najdete v tématu [Postupy: nastavení ladění a konfigurací vydání](../../debugger/how-to-set-debug-and-release-configurations.md).

4. Klikněte na možnost **Pokročilé možnosti kompilace**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="optimizations"></a>Optimalizace

Následující možnosti určují optimalizace, které mohou v některých případech zmenšit programový soubor, nastavit program rychleji nebo urychlit proces sestavení.

**Odebrat kontroly přetečení celých čísel**

Toto políčko je ve výchozím nastavení zaškrtnuté, aby se povolila kontrola přetečení celého čísla. Zaškrtnutím tohoto políčka odeberete kontrolu přetečení celých čísel. Pokud zaškrtnete toto políčko, mohou být výpočty typu Integer rychlejší. Pokud však odeberete kontrolu přetečení a přetečení kapacity datového typu, mohou být uloženy nesprávné výsledky bez vyvolání chyby.

Pokud jsou kontrolovány podmínky přetečení a celočíselná operace přeteče, <xref:System.OverflowException> je vyvolána výjimka. Pokud nejsou kontrolovány podmínky přetečení, celočíselná operace přetéká nevyvolává výjimku.

**Povolit optimalizace**

Toto políčko není ve výchozím nastavení zaškrtnuté, chcete-li zakázat optimalizace kompilátoru. Zaškrtnutím tohoto políčka povolíte optimalizace kompilátoru. Optimalizace kompilátoru usnadňují, rychlejší a efektivnější výstupní soubor. Vzhledem k tomu, že optimalizace způsobují změnu uspořádání kódu ve výstupním souboru, optimalizace kompilátoru můžou ztížit ladění.

 **Základní adresa knihovny DLL**

V tomto textovém poli se zobrazí výchozí základní adresa knihovny DLL v šestnáctkovém formátu. V knihovně tříd a v projektech knihovny ovládacích prvků lze pomocí tohoto textového pole zadat základní adresu, která má být použita při vytvoření knihovny DLL.

 **Generovat informace o ladění**

V seznamu vyberte možnost **žádná**, **Úplná**nebo **PDB** . **None** určuje, že nejsou vygenerovány žádné informace o ladění. **Full** určuje, zda mají být vygenerovány úplné informace o ladění a **pouze PDB** určuje, zda mají být vygenerovány pouze informace o ladění PDB. Výchozí hodnota této možnosti je **plná**.

## <a name="compilation-constants"></a>Konstanty kompilace

Konstanty podmíněné kompilace mají podobný účinek jako použití direktivy preprocesoru [#Const](/dotnet/visual-basic/language-reference/directives/const-directive) ve zdrojovém souboru s tím rozdílem, že definované konstanty jsou veřejné a platí pro všechny soubory v projektu. Můžete použít konstanty podmíněné kompilace společně s [#If... Then... #Else](/dotnet/visual-basic/language-reference/directives/if-then-else-directives) direktiva pro podmíněné kompilování zdrojových souborů. Viz [Podmíněná kompilace](/dotnet/visual-basic/programming-guide/program-structure/conditional-compilation).

 **Definovat konstantu DEBUG**

Ve výchozím nastavení je toto zaškrtávací políčko zaškrtnuto a určuje, že je nastavena konstanta ladění.

 **Definovat konstantu TRACE**

Ve výchozím nastavení je toto zaškrtávací políčko zaškrtnuto a určuje, že je nastavena konstanta trasování.

 **Vlastní konstanty**

Do tohoto textového pole zadejte libovolné vlastní konstanty pro vaši aplikaci. Položky by měly být odděleny čárkami, a to pomocí tohoto formuláře: **název1 = "hodnota1", název2 = "hodnota2", Název3 = "hodnota3"**.

## <a name="other-settings"></a>Další nastavení

**Generovat serializace sestavení**

Toto nastavení určuje, zda bude kompilátor vytvářet sestavení serializace XML. Sestavení serializace mohou zlepšit výkon při spuštění v <xref:System.Xml.Serialization.XmlSerializer> případě, že jste tuto třídu použili k serializaci typů ve vašem kódu. Výchozí hodnota této možnosti je **auto**. **Automaticky** určuje, že sestavení serializace budou generována pouze v případě, že jste použili <xref:System.Xml.Serialization.XmlSerializer> ke kódování typů v kódu do XML. **Off** určuje, že sestavení serializace nikdy nebyla vygenerována bez ohledu na to, zda váš kód používá <xref:System.Xml.Serialization.XmlSerializer> . **V** určuje, zda mají být sestavení serializace vždy vygenerována. Sestavení serializace jsou pojmenována `TypeName`.XmlSerializers.dll.

## <a name="see-also"></a>Viz také

- [Stránka Kompilovat, návrhář projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
