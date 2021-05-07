---
title: Stránka Sestavení, návrhář projektu (C#)
description: Naučte se používat stránku Sestavení v Návrháři projektu v Visual Studio k určení vlastností konfigurace sestavení projektu.
ms.custom: SEO-VS-2020
ms.date: 06/20/2017
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuild
helpviewer_keywords:
- Build options [C#]
- Project Designer, Build page
ms.assetid: 77ff1bfc-d633-4634-ba29-9afdb6d7e362
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 91b254f4c075693e23d8f650356cd97e86a4c746
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798554"
---
# <a name="build-page-project-designer-c"></a>Stránka Sestavení, návrhář projektu (C#)

Na stránce **Sestavení** v **Návrháři projektu** určete vlastnosti konfigurace sestavení projektu. Tato stránka se týká [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] pouze projektů.

Pokud chcete získat **přístup na** stránku Sestavení, zvolte uzel projektu (ne uzel Řešení) v **Průzkumník řešení**.  Pak v **nabídce** zvolte **Zobrazení** , Stránky vlastností. Jakmile se zobrazí Návrhář projektu, zvolte **kartu** Sestavení.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="configuration-and-platform"></a>Konfigurace a platforma

Následující možnosti umožňují vybrat konfiguraci a platformu, která se má zobrazit nebo upravit.

> [!NOTE]
> Díky zjednodušeným konfiguracím sestavení systém projektu určuje, jestli se má sestavit ladicí nebo vydá verze. Proto se tyto možnosti nezobrazí. Další informace najdete v tématu [Postupy: Nastavení konfigurace ladění a verzí.](../../debugger/how-to-set-debug-and-release-configurations.md)

**Konfigurace**

Určuje, která nastavení konfigurace se mají zobrazit nebo upravit. Nastavení může být **Aktivní (ladění)** (výchozí nastavení), **Ladění,** **Vydání** nebo **Všechny konfigurace.**

**Platforma**

Určuje, která nastavení platformy se mají zobrazit nebo upravit. Výchozí nastavení je **Aktivní (libovolný procesor).** Aktivní platformu můžete změnit pomocí **Správce konfigurace**. Další informace najdete v tématu [Postupy: Vytváření a úpravy konfigurací.](../../ide/how-to-create-and-edit-configurations.md)

## <a name="general"></a>Obecné

Následující možnosti umožňují nakonfigurovat několik nastavení kompilátoru jazyka C#.

**Symboly podmíněné kompilace**

Určuje symboly, na kterých se má provést podmíněná kompilace. Oddělte symboly středníkem (;). Další informace najdete v tématu [/define (Možnosti kompilátoru C#).](/dotnet/csharp/language-reference/compiler-options/define-compiler-option)

**Definování konstanty DEBUG**

Definuje DEBUG jako symbol ve všech souborech zdrojového kódu ve vaší aplikaci. Výběr této možnosti je stejný jako při `/define:DEBUG` použití možnosti příkazového řádku.

**Definování konstanty TRACE**

Definuje TRACE jako symbol ve všech souborech zdrojového kódu ve vaší aplikaci. Výběr této možnosti je stejný jako při `/define:TRACE` použití možnosti příkazového řádku.

**Cíl platformy**

Určuje procesor, na který bude výstupní soubor zacílený. Zvolte **x86** pro jakýkoli 32bitový procesor kompatibilní s Intelem, zvolte **x64** pro jakýkoli 64bitový procesor  kompatibilní s Intelem, zvolte **ARM** pro procesory ARM nebo zvolte Jakýkoli procesor a určete, že jakýkoli procesor je přijatelný. **Jakýkoli procesor** je výchozí hodnotou pro projekty, protože umožňuje spuštění aplikace na nejširší škále hardwaru.

Další informace najdete v tématu [/platform (možnosti kompilátoru C#).](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)

**Nullable**

Určuje kontext S možnou hodnotou null v jazyce C# pro celé projekty. Tato možnost uživatelského rozhraní byla zavedena v Visual Studio 16.5 a je povolená pouze pro projekty, které používají C# 8.0 nebo novější.

Další informace najdete v tématu [Kontexty s povolenou hodnotou Null.](/dotnet/csharp/nullable-references#nullable-contexts)

**Preferovat 32bitovou verzi**

Pokud je zaškrtnuté políčko **Preferovat32bitovou** verzi, aplikace se spustí jako 32bitová aplikace v 32bitové i 64bitové verzi Windows. Pokud políčko není zaškrtnuté, aplikace běží jako 32bitová aplikace v 32bitových verzích Windows a jako 64bitová aplikace v 64bitových verzích Windows.

Pokud aplikaci spouštíte jako 64ovou aplikaci, je velikost ukazatele Dvojitá a problémy s kompatibilitou můžou nastat i u jiných knihoven, které jsou výhradně 32 bitové. Je vhodné spustit 64ovou aplikaci pouze v případě, že potřebuje více než 4 GB paměti nebo 64 instrukcí, což přináší výrazné zlepšení výkonu.

Toto zaškrtávací políčko je k dispozici pouze v případě, že jsou splněné všechny následující podmínky:

- Na **stránce sestavení** je seznam **cílů platformy** nastavený na **Libovolný procesor**.

- Na **stránce aplikace** se v seznamu **Typ výstupu** určuje, že projekt je aplikace.

- Na **stránce aplikace** se v seznamu **cílový rámec** určuje .NET Framework 4,5.

**Povolení nezabezpečeného kódu**

Umožňuje kompilaci kódu, který používá klíčové slovo [unsafe](/dotnet/csharp/language-reference/keywords/unsafe) . Další informace naleznete v tématu [/unsafe (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option).

**Optimalizovat kód**

Povolte nebo zakažte optimalizace prováděné kompilátorem, abyste mohli zmenšit, rychleji a zefektivnit výstupní soubor. Další informace naleznete v tématu [/optimize (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option).

## <a name="errors-and-warnings"></a>Chyby a upozornění

Následující nastavení jsou použita ke konfiguraci chyb a možností upozornění pro proces sestavení.

**Úroveň upozornění**

Určuje úroveň, která se má zobrazit pro upozornění kompilátoru. Další informace naleznete v tématu [/warn (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option).

**Potlačení upozornění**

Blokuje schopnost kompilátoru generovat jedno nebo více upozornění. Více čísel upozornění oddělte čárkou nebo středníkem. Další informace naleznete v tématu [/nowarn (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option).

## <a name="treat-warnings-as-errors"></a>Zpracovávat upozornění jako chyby

Následující nastavení slouží k určení, která upozornění jsou považována za chyby. Vyberte jednu z následujících možností, která určuje, za jakých podmínek se má v případě, že se při sestavení vyskytne upozornění, vrátit chybu. Další informace naleznete v tématu [/warnaserror (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).

**None** – nezpracovává žádné výstrahy jako chyby.

**Vše** – zpracovává všechna upozornění jako chyby.

**Specifická upozornění** – zachází s zadanými upozorněními jako s chybami. Více čísel upozornění oddělte čárkou nebo středníkem.

> [!TIP]
> Pokud nechcete, aby upozornění analýzy kódu byla považována za chyby, přečtěte si téma [Nejčastější dotazy k analýze kódu](/visualstudio/code-quality/analyzers-faq#treat-warnings-as-errors).

## <a name="output"></a>Výstup

Následující nastavení se používají ke konfiguraci možností výstupu pro proces sestavení.

**Výstupní cesta**

Určuje umístění výstupních souborů pro tuto konfiguraci projektu. Do tohoto pole zadejte cestu k výstupu sestavení nebo klikněte na tlačítko **Procházet** a zadejte cestu. Cesta je relativní; Pokud zadáte absolutní cestu, bude uložena jako relativní. Výchozí cesta je bin\Debug nebo bin\Release \\ .

V případě zjednodušených konfigurací sestavení Určuje projektový systém, zda má být vytvořena verze ladění nebo vydání. Příkaz **Build** z nabídky **ladění** (F5) vloží sestavení do umístění ladění bez ohledu na **výstupní cestu** , kterou zadáte. Příkaz **Build** v nabídce **sestavení** však vloží do umístění, které zadáte. Další informace najdete v tématu [Principy konfigurací sestavení](../../ide/understanding-build-configurations.md).

**Soubor dokumentace XML**

Určuje název souboru, do kterého se budou zpracovávat komentáře k dokumentaci. Další informace najdete v tématu [/doc (možnosti kompilátoru C#).](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option)

**Registrace zprostředkovatele komunikace s objekty COM**

Označuje, že vaše spravovaná aplikace zpřístupní objekt COM (obálka volatelná modelem COM), která umožňuje, aby objekt COM komunikoval s vaší spravovanou aplikací. Vlastnost **Typ výstupu** [](../../ide/reference/application-page-project-designer-visual-basic.md) na stránce  Aplikace v Návrháři projektu  pro tuto aplikaci musí být nastavená na knihovnu tříd, aby byla vlastnost **Register for COM interop** dostupná. Příklad třídy, kterou můžete zahrnout do aplikace a zveřejnit jako objekt COM, naleznete v [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] části Příklad třídy [COM](/dotnet/csharp/programming-guide/interop/example-com-class).

**Generování sestavení serializace**

Určuje, zda bude kompilátor používat XML Serializer Generator Tool (Sgen.exe) k vytvoření sestavení serializace XML. Sestavení serializace může zlepšit výkon při spuštění, pokud jste použili třídu k serializaci <xref:System.Xml.Serialization.XmlSerializer> typů v kódu. Ve výchozím nastavení je tato možnost nastavena na **Hodnotu Auto**, která určuje, že sestavení serializace být generovány pouze v případě, že jste použili ke kódování typů v kódu <xref:System.Xml.Serialization.XmlSerializer> do XML. **Off** určuje, že sestavení serializace nikdy být generována, bez ohledu na to, zda váš kód používá <xref:System.Xml.Serialization.XmlSerializer> . **On** určuje, že sestavení serializace vždy být generovány. Sestavení serializace jsou `TypeName` pojmenována.XmlSerializers.dll. Další informace najdete v [XML Serializer Generator Tool (Sgen.exe).](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe)

**Pokročilý**

Kliknutím zobrazíte [dialogové okno Upřesnit nastavení sestavení (C#).](../../ide/reference/advanced-build-settings-dialog-box-csharp.md)

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k vlastnostem projektu](../../ide/reference/project-properties-reference.md)
- [Možnosti kompilátoru jazyka C#](/dotnet/csharp/language-reference/compiler-options/index)
