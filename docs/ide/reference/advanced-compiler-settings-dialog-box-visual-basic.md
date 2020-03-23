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
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9ebc2da5e71dbdee13df4cf658f3681804879f58
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596928"
---
# <a name="advanced-compiler-settings-dialog-box-visual-basic"></a>Dialogové okno Upřesnit nastavení kompilátoru (Visual Basic)

Dialogové okno **Upřesnit nastavení kompilátoru** **návrháře projektu** slouží k určení pokročilých vlastností konfigurace sestavení projektu. Toto dialogové okno platí pouze pro projekty jazyka Visual Basic.

## <a name="to-access-this-dialog-box"></a>Přístup k tomuto dialogovému oknu

1. V **Průzkumníku řešení**zvolte uzel projektu (nikoli uzel **Řešení).**

2. V nabídce **Project** klepněte na **položku Vlastnosti**. Po zobrazení **Návrháře projektů** klikněte na kartu **Kompilace.**

3. Na stránce Kompilace vyberte [Návrhář projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) **možnost Konfigurace** a **platforma**. Ve zjednodušených konfiguracích sestavení nejsou zobrazeny seznamy **konfigurace** a **platformy.** Další informace naleznete v [tématu How to: Set debug and release configurations](../../debugger/how-to-set-debug-and-release-configurations.md).

4. Klepněte na **položku Upřesnit možnosti kompilace**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="optimizations"></a>Optimalizace

Následující možnosti určují optimalizace, které mohou v některých případech zmenšit soubor programu, urychlit spuštění programu nebo urychlit proces sestavení.

**Odebrání kontrol přetekace celého čísla**

Toto políčko je ve výchozím nastavení zaškrtnuto, aby bylo možné povolit kontrolu přetečení celého čísla. Zaškrtnutím tohoto políčka odeberete kontrolu přetečení celého čísla. Pokud toto políčko zaškrtnete, mohou být výpočty celého čísla rychlejší. Pokud však odeberete kontrolu přetečení a přetečení kapacit y datového typu, mohou být uloženy nesprávné výsledky bez vyvolání chyby.

Pokud jsou zaškrtnuty podmínky přetečení a celá <xref:System.OverflowException> operace přetečení, je vyvolána výjimka. Pokud nejsou zaškrtnuté podmínky přetečení, přetečení operace celého čísla nevyvolá výjimku.

**Povolit optimalizace**

Toto políčko je ve výchozím nastavení vymazáno, aby bylo zakázáno optimalizace kompilátoru. Zaškrtnutím tohoto políčka povolíte optimalizaci kompilátoru. Optimalizace kompilátoru zmenšit, zrychlit a zefektivnit výstupní soubor. Protože však optimalizace způsobí, že přeuspořádání kódu ve výstupním souboru, optimalizace kompilátoru může ztížit ladění.

 **Základní adresa DLL**

Toto textové pole zobrazuje výchozí základní adresu dll v šestnáctkovém formátu. V projektech Knihovna tříd a Knihovna ovládacích prvku můžete pomocí tohoto textového pole určit základní adresu, která se má použít při vytváření knihovny DLL.

 **Generovat informace o ladění**

V seznamu vyberte **možnost Žádný**, **Úplný**nebo **pouze pdb.** **None** určuje, že nebudou generovány žádné informace o ladění. **Úplné** určuje, že budou generovány úplné informace o ladění a **pouze pdb** určuje, že by měly být generovány pouze informace o ladění PDB. Výchozí hodnota pro tuto možnost je **Úplná**.

## <a name="compilation-constants"></a>Konstanty kompilace

Konstanty podmíněné kompilace mají podobný účinek jako použití direktivy preprocesoru [#Const](/dotnet/visual-basic/language-reference/directives/const-directive) ve zdrojovém souboru, s tím rozdílem, že definované konstanty jsou veřejné a platí pro všechny soubory v projektu. Můžete použít konstanty podmíněné kompilace spolu s [#If... Potom... #Else](/dotnet/visual-basic/language-reference/directives/if-then-else-directives) direktivu ke podmíněné kompilaci zdrojových souborů. Viz [Podmíněná kompilace](/dotnet/visual-basic/programming-guide/program-structure/conditional-compilation).

 **Definovat konstantu LADĚNÍ**

Ve výchozím nastavení je toto políčko zaškrtnuto a určuje, že bude nastavena konstanta LADĚNÍ.

 **Definovat konstantu TRACE**

Ve výchozím nastavení je toto políčko zaškrtnuto a určuje, že bude nastavena konstanta TRACE.

 **Vlastní konstanty**

Do tohoto textového pole zadejte všechny vlastní konstanty pro vaši aplikaci. Položky by měly být odděleny čárkami pomocí tohoto formuláře: **Name1="Value1",Name2="Value2",Name3="Value3" .**

## <a name="other-settings"></a>Další nastavení

**Generovat sestavení serializace**

Toto nastavení určuje, zda kompilátor vytvoří sestavení serializace XML. Serializace sestavení můžete zlepšit výkon <xref:System.Xml.Serialization.XmlSerializer> při spuštění, pokud jste použili tuto třídu serializovat typy v kódu. Výchozí hodnota pro tuto možnost je **Automaticky**. **Auto** určuje, že serializační sestavení budou generována <xref:System.Xml.Serialization.XmlSerializer> pouze v případě, že jste použili ke kódování typů v kódu do jazyka XML. **Off** určuje, že serializační sestavení nikdy být generovány, <xref:System.Xml.Serialization.XmlSerializer>bez ohledu na to, zda váš kód používá . **On** určuje, že serializační sestavení vždy generována. Serializační sestavení jsou `TypeName`pojmenována . Soubor XmlSerializers.dll.

## <a name="see-also"></a>Viz také

- [Stránka Kompilovat, návrhář projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
