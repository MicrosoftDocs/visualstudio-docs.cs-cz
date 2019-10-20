---
title: Dialogové okno Upřesnit nastavení kompilátoru (Visual Basic) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAdvancedCompile
helpviewer_keywords:
- Advanced Compiler Settings dialog box
ms.assetid: 1f81133a-293f-4dba-bc1c-8baafb01d857
caps.latest.revision: 52
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ba666b0ff5544b185f82a66c78d6259e9f1268fd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651771"
---
# <a name="advanced-compiler-settings-dialog-box-visual-basic"></a>Dialogové okno Upřesnit nastavení kompilátoru (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pomocí dialogového okna **Nastavení AdvancedCompiler** **Návrháře projektu** můžete zadat rozšířené vlastnosti konfigurace sestavení projektu. Toto dialogové okno se vztahuje pouze na Visual Basic projekty.

### <a name="to-access-this-dialog-box"></a>Přístup k tomuto dialogovému oknu

1. V **Průzkumník řešení**vyberte uzel projektu (ne uzel **řešení** ).

2. V nabídce **projekt** klikněte na příkaz **vlastnosti**. Když se zobrazí **Návrhář projektu** , klikněte na kartu **kompilovat** .

3. Na [stránce kompilovat Návrháře projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)vyberte **konfiguraci** a **platformu**. Ve zjednodušených konfiguracích sestavení se nezobrazí seznamy **konfigurací** a **platforem** . Další informace naleznete v tématu [Konfigurace projektů ladění a vydávání](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

4. Klikněte na možnost **Pokročilé možnosti kompilace**.

   [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

## <a name="optimizations"></a>Optimalizace
 Následující možnosti určují optimalizace, které mohou v některých případech zmenšit programový soubor, nastavit program rychleji nebo urychlit proces sestavení.

 **Odebrat kontroly přetečení celých čísel** Ve výchozím nastavení je toto políčko zaškrtnuté, aby se povolila kontrola přetečení celého čísla. Zaškrtnutím tohoto políčka odeberete kontrolu přetečení celých čísel. Pokud zaškrtnete toto políčko, mohou být výpočty typu Integer rychlejší. Pokud však odeberete kontrolu přetečení a přetečení kapacity datového typu, mohou být uloženy nesprávné výsledky bez vyvolání chyby.

 Pokud jsou kontrolovány podmínky přetečení a celočíselná operace přeteče, je vyvolána výjimka <xref:System.OverflowException>. Pokud nejsou kontrolovány podmínky přetečení, celočíselná operace přetéká nevyvolává výjimku.

 **Povolit optimalizace** Ve výchozím nastavení je toto políčko zaškrtnuté, pokud chcete zakázat optimalizace kompilátoru. Zaškrtnutím tohoto políčka povolíte optimalizace kompilátoru. Optimalizace kompilátoru usnadňují, rychlejší a efektivnější výstupní soubor. Vzhledem k tomu, že optimalizace způsobují změnu uspořádání kódu ve výstupním souboru, optimalizace kompilátoru můžou ztížit ladění.

 **Základní adresa knihovny DLL** V tomto textovém poli se zobrazí výchozí základní adresa knihovny DLL v šestnáctkovém formátu. V knihovně tříd a v projektech knihovny ovládacích prvků lze pomocí tohoto textového pole zadat základní adresu, která má být použita při vytvoření knihovny DLL.

 **Generovat informace o ladění** V seznamu vyberte možnost **žádná**, **Úplná**nebo **PDB** . **None** určuje, že nejsou vygenerovány žádné informace o ladění. **Full** určuje, zda mají být vygenerovány úplné informace o ladění a **pouze PDB** určuje, že budou vygenerovány pouze informace o ladění PDB. Ve výchozím nastavení je tato možnost nastavena na hodnotu **Full (plná**).

## <a name="compilation-constants"></a>Konstanty kompilace
 Konstanty podmíněné kompilace mají podobný účinek jako použití direktivy preprocesoru [#Const](https://msdn.microsoft.com/library/707669e5-23f9-4f17-8622-a0d534429386) ve zdrojovém souboru s tím rozdílem, že definované konstanty jsou veřejné a platí pro všechny soubory v projektu. Můžete použít konstanty podmíněné kompilace společně s [#If... Then... #Else](https://msdn.microsoft.com/library/10bba104-e3fd-451b-b672-faa472530502) direktiva pro podmíněné kompilování zdrojových souborů. Viz [Podmíněná kompilace](https://msdn.microsoft.com/library/9c35e55e-7eee-44fb-a586-dad1f1884848).

 **Definovat konstantu Debug** Ve výchozím nastavení je toto zaškrtávací políčko zaškrtnuto a určuje, že je nastavena konstanta ladění.

 **Definovat konstantu Trace** Ve výchozím nastavení je toto zaškrtávací políčko zaškrtnuto a určuje, že je nastavena konstanta trasování.

 **Vlastní konstanty** Do tohoto textového pole zadejte libovolné vlastní konstanty pro vaši aplikaci. Položky by měly být odděleny čárkami, a to pomocí tohoto formuláře: **název1 = "hodnota1", název2 = "hodnota2", Název3 = "hodnota3"** .

## <a name="other-settings"></a>Další nastavení
 **Generovat serializace sestavení** Toto nastavení určuje, zda bude kompilátor vytvářet sestavení serializace XML. Sestavení serializace mohou zlepšit výkon při spuštění <xref:System.Xml.Serialization.XmlSerializer>, pokud jste tuto třídu použili k serializaci typů ve vašem kódu. Ve výchozím nastavení je tato možnost nastavena na hodnotu **auto**, která určuje, že sestavení serializace budou generována pouze v případě, že jste použili <xref:System.Xml.Serialization.XmlSerializer> ke kódování typů v kódu do XML. **Off** určuje, že sestavení serializace nikdy nebyla vygenerována bez ohledu na to, zda váš kód používá <xref:System.Xml.Serialization.XmlSerializer>. **V** určuje, zda mají být sestavení serializace vždy vygenerována. Sestavení serializace jsou pojmenovány `TypeName`. XmlSerializers. dll.

## <a name="see-also"></a>Viz také
 [Stránka Kompilovat, Návrhář projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
