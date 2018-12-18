---
title: Stránka Sestavení, návrhář projektu (C#)
ms.date: 06/20/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuild
helpviewer_keywords:
- Build options [C#]
- Project Designer, Build page
ms.assetid: 77ff1bfc-d633-4634-ba29-9afdb6d7e362
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: b003b3f965ab4f3857e2a532ae715d99533aa8e7
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38783815"
---
# <a name="build-page-project-designer-c"></a>Stránka Sestavení, návrhář projektu (C#)
Použití **sestavení** stránku **Návrháře projektu** k určení vlastností konfigurace sestavení projektu. Tato stránka se vztahuje na [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] pouze pro projekty.

Pro přístup k **sestavení** zvolte uzel projektu (ne **řešení** uzlu) v **Průzkumníka řešení**. Klikněte na tlačítko **zobrazení**, **stránky vlastností** v nabídce. Jakmile se zobrazí Návrhář projektu, zvolte **sestavení** kartu.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="configuration-and-platform"></a>Konfigurace a platforma
Tyto možnosti umožňují vybrat konfigurace a platformy k zobrazení a úpravě.

> [!NOTE]
> Pomocí zjednodušených konfigurací sestavení systém projektu určuje, jestli se má sestavení ladění nebo vydání verze. Proto nejsou tyto možnosti zobrazeny. Další informace najdete v tématu [postupy: nastavení ladění a vydání konfigurace](../../debugger/how-to-set-debug-and-release-configurations.md).

**Konfigurace** určuje které nastavení konfigurace má být zobrazeno nebo upraveno. Toto nastavení může být **aktivní (ladění)** (Toto je výchozí), **ladění**, **vydání**, nebo **všechny konfigurace**.

**Platforma** určuje které nastavení platformy má být zobrazeno nebo upraveno. Ve výchozím nastavení **aktivní (jakýkoli procesor)**. Můžete změnit aktivní platformu pomocí **nástroje Configuration Manager**. Další informace najdete v tématu [postupy: vytvoření a úprava konfigurací](../../ide/how-to-create-and-edit-configurations.md).

## <a name="general"></a>Obecné
Tyto možnosti umožňují konfigurovat několik nastavení kompilátoru jazyka C#.

**Symboly podmíněné kompilace** určuje symboly, s nimiž se má provést Podmíněná kompilace. Symboly oddělte středníkem (";"). Další informace najdete v tématu [/ define (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option).

**Definovat konstantu DEBUG** definuje DEBUG jako symbol ve zdrojovém kódu všechny soubory ve vaší aplikaci. Tento výběr je ekvivalentní k použití `/define:DEBUG` možnost příkazového řádku.

**Definovat konstantu TRACE** definuje TRACE jako symbol ve zdrojovém kódu všechny soubory ve vaší aplikaci. Tento výběr je ekvivalentní k použití `/define:TRACE` možnost příkazového řádku.

**Cílová platforma** Určuje procesor, který bude cílen výstupním souborem. Zvolte **x86** jakýkoli procesor kompatibilní s verzí Intel 32-bit, zvolte **x64** jakýkoli procesor kompatibilní s verzí Intel 64-bit, zvolte **ARM** pro procesory ARM, nebo zvolte  **Jakýkoli procesor** k určení, že je přijatelný jakýkoli procesor. **Jakýkoli procesor** je výchozí hodnota pro projekty, protože umožňuje aplikaci, aby běžela v nejširší škále hardwaru.

Další informace najdete v tématu [/Platform (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option).

**Preferovat 32bitovou verzi** Pokud **preferovat 32bitovou verzi** zaškrtávací políčko zaškrtnuto, aplikace běží jako 32bitová aplikace ve 32bitové a 64bitové verze Windows. Pokud políčko není zaškrtnuto, aplikace běží jako 32bitová aplikace ve 32bitové verze Windows a jako na 64bitovými verzemi Windows 64-bit aplikace.

Pokud spustíte aplikaci jako 64bitovou aplikaci, zdvojnásobí se velikost ukazatele, a může dojít k problémům kompatibilita s ostatními knihovnami, které jsou výhradně 32bitové. Je vhodné spouštět 64bitovou aplikaci pouze v případě, že potřebuje více než 4 GB paměti nebo 64bitové instrukce poskytují významné výkonnostní zlepšení.

Toto zaškrtávací políčko je dostupné jenom v případě, že jsou splněny všechny následující podmínky:

-   Na **sestavit stránku**, **Cílová platforma** seznamu je nastavena na **jakýkoli procesor**.

-   Na **stránky aplikace**, **typ výstupu** seznam určuje, že projekt je aplikace.

-   Na **stránky aplikace**, **Cílová architektura** seznamu určuje rozhraní .NET Framework 4.5.


**Povolit nezabezpečený kód** umožňuje kód, který používá [nebezpečné](/dotnet/csharp/language-reference/keywords/unsafe) ke kompilaci klíčové slovo. Další informace najdete v tématu [/ unsafe (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option).

**Optimalizovat kód** povolte nebo zakažte optimalizace prováděné kompilátorem, aby výstupní soubor menší, rychlejší a efektivnější. Další informace najdete v tématu [/ optimize (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option).

## <a name="errors-and-warnings"></a>Chyby a upozornění
Následující nastavení se používají ke konfiguraci chyby a upozornění možnosti procesu sestavení.

**Úroveň upozornění** upřesňuje úroveň zobrazení upozornění kompilátoru. Další informace najdete v tématu [/ warn (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option).

**Potlačení upozornění** blokuje možnost kompilátoru generovat jedno nebo více upozornění. Více čísel upozornění oddělte čárkou nebo středníkem. Další informace najdete v tématu [/nowarn (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option).

## <a name="treat-warnings-as-errors"></a>Zpracovávat upozornění jako chyby
Tato nastavení slouží k určení, která upozornění jsou považována za chyby. Vyberte jednu z následujících možností pro označení podmínek pro vrácení chyby, když sestavení narazí na upozornění. Další informace najdete v tématu [/warnaserror (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).

**Žádný** nezpracovává žádná upozornění jako chyby.

**Specifická upozornění** zachází s určenými varováními jako s chybami. Více čísel upozornění oddělte čárkou nebo středníkem.

**Všechny** zpracuje všechna upozornění jako chyby.

## <a name="output"></a>Výstup
Následující nastavení se používají ke konfiguraci možností výstupu pro proces sestavení.

**Výstupní cesta** Určuje umístění výstupních souborů pro tuto konfiguraci projektu. Zadejte cestu k výstupu sestavení v tomto poli, nebo zvolte **Procházet** tlačítko a zadejte cestu. Všimněte si, že cesta je relativní; Pokud zadáte absolutní cestu, bude uložena jako relativní. Výchozí cesta je bin\Debug nebo bin\Release\\.

Pomocí zjednodušených konfigurací sestavení systém projektu určuje, jestli se má sestavení ladění nebo vydání verze. **Sestavení** příkaz **ladění** nabídky (F5) vloží sestavení do místa ladění bez ohledu na to **výstupní cesta** zadáte. Ale **sestavení** příkaz **sestavení** nabídky se vloží do umístění, které zadáte. Další informace najdete v tématu [Principy konfigurací sestavení](../../ide/understanding-build-configurations.md).

**Soubor dokumentace XML** Určuje název souboru, do které dokumentace se zpracuje komentáře. Další informace najdete v tématu [/DOC (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option).

**Zaregistrovat pro interoperabilitu COM** označuje, že bude vaše spravovaná aplikace vystavovat objekt modelu COM (Obálka volatelná aplikacemi COM) umožňující objektu modelu COM interakci s vaší spravovanou aplikací. **Typ výstupu** vlastnost [stránky aplikace](../../ide/reference/application-page-project-designer-visual-basic.md) z **Návrháře projektu** pro tuto aplikaci musí být nastaven na hodnotu **knihovny tříd** v pořadí **zaregistrovat pro interoperabilitu COM** vlastnost k dispozici. Příklad třídy, které můžete zahrnout do vaší [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] aplikace a použít jako objekt modelu COM naleznete v tématu [Ukázka třídy COM](/dotnet/csharp/programming-guide/interop/example-com-class).

**Generovat sestavení serializace** Určuje, zda kompilátor použije nástroj generátoru Serializéru XML (Sgen.exe) k tvorbě XML serializace sestavení. Sestavení serializace mohou zvýšit výkon při spuštění <xref:System.Xml.Serialization.XmlSerializer> Pokud jste již použili k serializaci typů ve vašem kódu. Ve výchozím nastavení je tato možnost nastavená na **automaticky**, která určuje, že se serializace sestavení vytvoří pouze v případě, že jste už použili <xref:System.Xml.Serialization.XmlSerializer> ke kódování typů ve vašem kódu pro XML. **Vypnout** Určuje, že sestavení serializace nebudou nikdy generována, bez ohledu na to, jestli váš kód používá <xref:System.Xml.Serialization.XmlSerializer>. **Na** Určuje, že sestavení serializace budou vždy generována. Jsou pojmenované sestavení serializace `TypeName`. XmlSerializers.dll. Další informace najdete v tématu [nástroj XML Serializer Generator (Sgen.exe)](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe).

**Upřesnit** zobrazíte klepnutím [pokročilé vytváření dialogové okno nastavení (C#)](../../ide/reference/advanced-build-settings-dialog-box-csharp.md) dialogové okno.

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k vlastnostem projektu](../../ide/reference/project-properties-reference.md)
- [Možnosti kompilátoru jazyka C#](/dotnet/csharp/language-reference/compiler-options/index)