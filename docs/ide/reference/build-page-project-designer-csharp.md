---
title: Stránka Sestavení, návrhář projektu (C#)
ms.date: 06/20/2017
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuild
helpviewer_keywords:
- Build options [C#]
- Project Designer, Build page
ms.assetid: 77ff1bfc-d633-4634-ba29-9afdb6d7e362
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 85bf50c653d82a7de22d5a81fd81c38db0db1be8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76923269"
---
# <a name="build-page-project-designer-c"></a>Stránka Sestavení, návrhář projektu (C#)

Pomocí stránky **Sestavení** **návrháře projektu** určete vlastnosti konfigurace sestavení projektu. Tato stránka se [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] vztahuje pouze na projekty.

Chcete-li získat přístup k stránce **Sestavení,** zvolte uzel projektu (nikoli uzel **řešení)** v **Průzkumníku řešení**. Pak v nabídce zvolte **Zobrazit** **, Stránky vlastností.** Když se zobrazí Návrhář projektu, zvolte kartu **Sestavení.**

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="configuration-and-platform"></a>Konfigurace a platforma

Následující možnosti umožňují vybrat konfiguraci a platformu, kterou chcete zobrazit nebo upravit.

> [!NOTE]
> U zjednodušených konfigurací sestavení systém projektu určuje, zda má být konto kvytvoření ladicí nebo vydané verze. Proto tyto možnosti nejsou zobrazeny. Další informace naleznete v [tématu How to: Set debug and release configurations](../../debugger/how-to-set-debug-and-release-configurations.md).

**Konfigurace**

Určuje, která nastavení konfigurace se mají zobrazit nebo upravit. Nastavení může být **Aktivní (Ladění)** (toto je výchozí), **Ladění**, **Vydání**nebo **Všechny konfigurace**.

**Platforma**

Určuje, které nastavení platformy se má zobrazit nebo upravit. Výchozí nastavení je **Aktivní (Libovolný procesor).** Aktivní platformu můžete změnit pomocí **nástroje Configuration Manager**. Další informace naleznete v [tématu How to: Create and Edit Configurations](../../ide/how-to-create-and-edit-configurations.md).

## <a name="general"></a>Obecné

Následující možnosti umožňují nakonfigurovat několik nastavení kompilátoru jazyka C#.

**Symboly podmíněné kompilace**

Určuje symboly, na kterých má být provedena podmíněná kompilace. Samostatné symboly s středníkem (";"). Další informace naleznete v tématu [/define (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option).

**Definovat konstantu LADĚNÍ**

Definuje ladění jako symbol ve všech zdrojových kódových souborech ve vaší aplikaci. Výběr této možnosti je `/define:DEBUG` ekvivalentní použití možnosti příkazového řádku.

**Definovat konstantu TRACE**

Definuje trasování jako symbol ve všech zdrojových kódových souborech ve vaší aplikaci. Výběr této možnosti je `/define:TRACE` ekvivalentní použití možnosti příkazového řádku.

**Cíl platformy**

Určuje procesor, na který má výstupní soubor cílit. Zvolte **x86** pro libovolný 32bitový procesor kompatibilní s procesorem Intel, zvolte **x64** pro libovolný 64bitový procesor kompatibilní s procesorem Intel, zvolte **ARM** pro procesory ARM nebo zvolte libovolný procesor a **určete,** že jakýkoli procesor je přijatelný. **Libovolný procesor** je výchozí hodnota pro projekty, protože umožňuje aplikaci spustit na nejširší rozsah hardwaru.

Další informace naleznete v tématu [/platform (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option).

**Vynulovatelné**

Určuje kontext s možnou hodnotou null celého projektu c#. Tato možnost uj.

Další informace naleznete [v tématu Nullable Contexts](/dotnet/csharp/nullable-references#nullable-contexts).

**Preferujte 32bitové**

Pokud je zaškrtnuté políčko **Prefer32bit,** aplikace se spustí jako 32bitová aplikace v 32bitových i 64bitových verzích systému Windows. Pokud políčko není zaškrtnuto, aplikace se spustí jako 32bitová aplikace v 32bitových verzích systému Windows a jako 64bitová aplikace v 64bitových verzích systému Windows.

Pokud spustíte aplikaci jako 64bitovou aplikaci, velikost ukazatele se zdvojnásobí a problémy s kompatibilitou mohou nastat u jiných knihoven, které jsou výhradně 32bitové. Je užitečné spustit 64bitovou aplikaci pouze v případě, že potřebuje více než 4 GB paměti nebo 64bitové pokyny poskytují významné zlepšení výkonu.

Toto zaškrtávací políčko je k dispozici pouze v případě, že jsou splněny všechny následující podmínky:

- Na **stránce sestavení**je cílový seznam **platformy** nastaven na **libovolný procesor**.

- Na **stránce aplikace**určuje seznam **Typ výstupu,** že projekt je aplikace.

- Na **stránce aplikace**určuje seznam **Cílová architektura** rozhraní .NET Framework 4.5.

**Povolit nebezpečný kód**

Umožňuje kód, který používá [nebezpečné](/dotnet/csharp/language-reference/keywords/unsafe) klíčové slovo ke kompilaci. Další informace naleznete v tématu [/unsafe (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option).

**Optimalizovat kód**

Povolte nebo zakažte optimalizace prováděné kompilátorem, aby byl výstupní soubor menší, rychlejší a efektivnější. Další informace naleznete v tématu [/optimize (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option).

## <a name="errors-and-warnings"></a>Chyby a upozornění

Následující nastavení slouží ke konfiguraci chyby a upozornění možnosti pro proces sestavení.

**Úroveň varování**

Určuje úroveň, která se má zobrazit pro upozornění kompilátoru. Další informace naleznete v tématu [/warn (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option).

**Potlačení upozornění**

Blokuje schopnost kompilátoru generovat jedno nebo více upozornění. Oddělte více výstražných čísel čárkou nebo středníkem. Další informace naleznete [v tématu /nowarn (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option).

## <a name="treat-warnings-as-errors"></a>Považovat upozornění za chyby

Následující nastavení slouží k určení, která upozornění jsou považována za chyby. Vyberte jednu z následujících možností, která označuje, za jakých podmínek má být vrácena chyba, když sestavení narazí na upozornění. Další informace naleznete v tématu [/warnaserror (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).

**Žádný** - Nepovažuje žádná upozornění za chyby.

**Vše** - Považuje všechna upozornění za chyby.

**Konkrétní upozornění** - Zachází zadané upozornění jako chyby. Oddělte více výstražných čísel čárkou nebo středníkem.

> [!TIP]
> Pokud nechcete, aby se upozornění na analýzu kódu považovala za chyby, přečtěte [si otázky nejčastějších dotazů k analýze kódu](../../code-quality/analyzers-faq.md#treat-warnings-as-errors).

## <a name="output"></a>Výstup

Následující nastavení slouží ke konfiguraci výstupních možností pro proces sestavení.

**Výstupní cesta**

Určuje umístění výstupních souborů pro konfiguraci tohoto projektu. Do tohoto pole zadejte cestu výstupu sestavení nebo zvolte tlačítko **Procházet** a určete cestu. Cesta je relativní; pokud zadáte absolutní cestu, bude uložena jako relativní. Výchozí cesta je bin\Debug nebo\\bin\Release .

U zjednodušených konfigurací sestavení systém projektu určuje, zda má být konto kvytvoření ladicí nebo vydané verze. Příkaz **Sestavení** z nabídky **Ladění** (F5) vloží sestavení do umístění ladění bez ohledu na zadanou **výstupní cestu.** Příkaz **Sestavení** z nabídky **Sestavení** jej však umístí do zadaného umístění. Další informace naleznete [v tématu Principy konfigurace sestavení](../../ide/understanding-build-configurations.md).

**Soubor dokumentace XML**

Určuje název souboru, do kterého budou zpracovány komentáře dokumentace. Další informace naleznete v tématu [/doc (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option).

**Zaregistrovat se pro interop COM**

Označuje, že spravovaná aplikace zpřístupní objekt COM (taelný obálku com), který umožňuje objektu COM pracovat se spravovanou aplikací. Vlastnost **Output type** na stránce [Aplikace](../../ide/reference/application-page-project-designer-visual-basic.md) **Návrháře projektu** pro tuto aplikaci musí být nastavena na **knihovnu tříd,** aby byla dostupná vlastnost **Register for COM interop.** Příklad třídy, kterou můžete [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] zahrnout do aplikace a vystavit jako objekt COM, naleznete v [tématu Příklad třídy COM](/dotnet/csharp/programming-guide/interop/example-com-class).

**Generovat sestavení serializace**

Určuje, zda bude kompilátor používat nástroj generátor serializátorů XML (Sgen.exe) k vytvoření sestavení serializace XML. Serializace sestavení můžete zlepšit výkon <xref:System.Xml.Serialization.XmlSerializer> při spuštění, pokud jste použili tuto třídu serializovat typy v kódu. Ve výchozím nastavení je tato možnost nastavena na **hodnotu Automaticky**, která <xref:System.Xml.Serialization.XmlSerializer> určuje, že sestavení serializace budou generována pouze v případě, že jste použili ke kódování typů v kódu do jazyka XML. **Off** určuje, že serializační sestavení nikdy být generovány, <xref:System.Xml.Serialization.XmlSerializer>bez ohledu na to, zda váš kód používá . **On** určuje, že serializační sestavení vždy generována. Serializační sestavení jsou `TypeName`pojmenována . Soubor XmlSerializers.dll. Další informace naleznete v tématu [XML Serializer Generator Tool (Sgen.exe).](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe)

**Pokročilé**

Klepnutím zobrazíte dialogové [okno Rozšířené nastavení sestavení (C#).](../../ide/reference/advanced-build-settings-dialog-box-csharp.md)

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k vlastnostem projektu](../../ide/reference/project-properties-reference.md)
- [Možnosti kompilátoru jazyka C#](/dotnet/csharp/language-reference/compiler-options/index)
