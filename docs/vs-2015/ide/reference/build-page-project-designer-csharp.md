---
title: Stránka sestavení, Návrhář projektu (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuild
helpviewer_keywords:
- Build options [C#]
- Project Designer, Build page
ms.assetid: 77ff1bfc-d633-4634-ba29-9afdb6d7e362
caps.latest.revision: 47
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 21b572e99d23c882f90a1e9218e7a52fb94aedb8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660912"
---
# <a name="build-page-project-designer-c"></a>Stránka Sestavení, návrhář projektu (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pomocí stránky **sestavení** **Návrháře projektu** Určete vlastnosti konfigurace sestavení projektu. Tato stránka se vztahuje pouze na [!INCLUDE[csprcs](../../includes/csprcs-md.md)] projekty.

 Pro přístup na stránku **sestavení** vyberte uzel projektu (nikoli uzel **řešení** ) v **Průzkumník řešení**. Pak zvolte **projekt**, **vlastnosti** na řádku nabídek. Když se zobrazí Návrhář projektu, klikněte na kartu **sestavení** .

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

## <a name="configuration-and-platform"></a>Konfigurace a platforma
 Následující možnosti umožňují vybrat konfiguraci a platformu pro zobrazení nebo úpravu.

> [!NOTE]
> V případě zjednodušených konfigurací sestavení Určuje projektový systém, zda má být vytvořena verze ladění nebo vydání. Proto tyto možnosti nejsou zobrazeny. Další informace naleznete v tématu [Konfigurace projektů ladění a vydávání](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

 **Konfigurace** Určuje, která nastavení konfigurace se mají zobrazit nebo upravit. Nastavení může být **aktivní (ladění)** (Toto je výchozí nastavení), **ladění**, **vydání**nebo **všechny konfigurace**.

 **Platforma** Určuje, která nastavení platformy se mají zobrazit nebo upravit. Výchozí nastavení je **aktivní (libovolný procesor)** . Aktivní platformu můžete změnit pomocí **Configuration Manager**. Další informace najdete v tématu [Postup: vytváření a úpravy konfigurací](../../ide/how-to-create-and-edit-configurations.md).

## <a name="general"></a>Obecné
 Následující možnosti umožňují nakonfigurovat několik C# nastavení kompilátoru.

 **Symboly podmíněné kompilace** Určuje symboly, na kterých se má provést Podmíněná kompilace. Symboly oddělujte středníkem (";"). Další informace naleznete v tématu [/define (C# možnosti kompilátoru)](https://msdn.microsoft.com/library/f17d7b4d-82d0-4133-8563-68cced1cac6e).

 **Definovat konstantu Debug** Definuje ladění jako symbol ve všech souborech zdrojového kódu ve vaší aplikaci. Tento výběr je ekvivalentní k použití možnosti příkazového řádku `/define:DEBUG`.

 **Definovat konstantu Trace** Definuje TRACE jako symbol ve všech souborech zdrojového kódu ve vaší aplikaci. Tento výběr je ekvivalentní k použití možnosti příkazového řádku `/define:TRACE`.

 **Cílový procesor** Určuje procesor, na který má výstupní soubor cílit. Zvolte **x86** pro libovolný 32 procesor kompatibilní s procesorem Intel, zvolte **x64** pro libovolný 64 procesor kompatibilního s procesorem Intel, zvolte **ARM** pro PROCESORy ARM nebo zvolte **Libovolný procesor** , abyste určili, že je přípustný libovolný procesor. **Libovolný procesor** je výchozí hodnota pro projekty, protože umožňuje aplikaci běžet na nejširší škále hardwaru.

 Další informace naleznete v tématu [/Platform (C# možnosti kompilátoru)](https://msdn.microsoft.com/library/c290ff5e-47f4-4a85-9bb3-9c2525b0be04).

 **Preferovat 32 – bit** Pokud je zaškrtnuto políčko **Prefer32-bit** , aplikace běží jako 32ová aplikace v 32 i v 64 bitových verzích systému Windows. Pokud políčko není zaškrtnuto, aplikace bude spuštěna jako 32ská aplikace v 32 verzích systému Windows a jako aplikace 64 64 v systému Windows v 16bitovém verzích.

 Pokud aplikaci spouštíte jako 64ovou aplikaci, je velikost ukazatele Dvojitá a problémy s kompatibilitou můžou nastat i u jiných knihoven, které jsou výhradně 32 bitové. Je vhodné spustit 64ovou aplikaci pouze v případě, že potřebuje více než 4 GB paměti nebo 64 instrukcí, což přináší výrazné zlepšení výkonu.

 Toto zaškrtávací políčko je k dispozici pouze v případě, že jsou splněné všechny následující podmínky:

- Na **stránce sestavení**je seznam **cílů platformy** nastavený na **Libovolný procesor**.

- Na **stránce aplikace**se v seznamu **Typ výstupu** určuje, že projekt je aplikace.

- Na **stránce aplikace**se v seznamu **cílový rámec** určuje .NET Framework 4,5.

  **Povolení nezabezpečeného kódu** Umožňuje kompilaci kódu, který používá klíčové slovo [unsafe](https://msdn.microsoft.com/library/7e818009-1c6e-4b9e-b769-3728a01586a0) . Další informace naleznete v tématu [/unsafe (C# možnosti kompilátoru)](https://msdn.microsoft.com/library/fdb77ed9-da03-45bd-bb7f-250704da1bcc).

  **Optimalizovat kód** Povolte nebo zakažte optimalizace prováděné kompilátorem, abyste mohli zmenšit, rychleji a zefektivnit výstupní soubor. Další informace naleznete v tématu [/optimize (C# možnosti kompilátoru)](https://msdn.microsoft.com/library/6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0).

## <a name="errors-and-warnings"></a>Chyby a upozornění
 Následující nastavení jsou použita ke konfiguraci chyb a možností upozornění pro proces sestavení.

 **Úroveň upozornění** Určuje úroveň, která se má zobrazit pro upozornění kompilátoru. Další informace naleznete v tématu [/warn (C# možnosti kompilátoru)](https://msdn.microsoft.com/library/5f80ff59-4991-4382-9f9a-77da18446e71).

 **Potlačit upozornění** Blokuje schopnost kompilátoru generovat jedno nebo více upozornění. Více čísel upozornění oddělte čárkou nebo středníkem. Další informace naleznete v tématu [/nowarn (C# možnosti kompilátoru)](https://msdn.microsoft.com/library/6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4).

## <a name="treat-warnings-as-errors"></a>Zpracovávat upozornění jako chyby
 Následující nastavení slouží k určení, která upozornění jsou považována za chyby. Vyberte jednu z následujících možností, která určuje, za jakých podmínek se má v případě, že se při sestavení vyskytne upozornění, vrátit chybu. Další informace naleznete v tématu [/warnaserror (C# možnosti kompilátoru)](https://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).

 **Žádné** Nezpracovává žádná upozornění jako chyby.

 **Konkrétní upozornění** Zpracovává zadaná upozornění jako chyby. Více čísel upozornění oddělte čárkou nebo středníkem.

 **Vše** Zpracovává všechna upozornění jako chyby.

## <a name="output"></a>Výstup
 Následující nastavení se používají ke konfiguraci možností výstupu pro proces sestavení.

 **Výstupní cesta** Určuje umístění výstupních souborů pro tuto konfiguraci projektu. Do tohoto pole zadejte cestu k výstupu sestavení nebo klikněte na tlačítko **Procházet** a zadejte cestu. Všimněte si, že cesta je relativní; Pokud zadáte absolutní cestu, bude uložena jako relativní. Výchozí cesta je bin\Debug nebo bin\Release \\. Další informace naleznete v tématu [Konfigurace projektů ladění a vydávání](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

 V případě zjednodušených konfigurací sestavení Určuje projektový systém, zda má být vytvořena verze ladění nebo vydání. Příkaz **Build** z nabídky **ladění** (F5) vloží sestavení do umístění ladění bez ohledu na **výstupní cestu** , kterou zadáte. Příkaz **Build** v nabídce **sestavení** však vloží do umístění, které zadáte. Další informace naleznete v tématu [Konfigurace projektů ladění a vydávání](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

 **Soubor dokumentace XML** Určuje název souboru, do kterého se budou zpracovávat komentáře k dokumentaci. Další informace naleznete v tématu [/doc (C# možnosti kompilátoru)](https://msdn.microsoft.com/library/849eea59-c936-4311-bad8-d07404480f2a).

 **Registrovat pro zprostředkovatele komunikace s objekty COM** Označuje, že vaše spravovaná aplikace bude vystavovat objekt COM (obálka s možnou sadou COM), která umožňuje objektu COM pracovat s vaší spravovanou aplikací. Vlastnost **Typ výstupu** na [stránce aplikace](../../ide/reference/application-page-project-designer-visual-basic.md) **Návrháře projektu** pro tuto aplikaci je nutné nastavit na **knihovnu tříd** , aby byla k dispozici vlastnost **Register pro zprostředkovatele komunikace s objekty COM** . Pro ukázkovou třídu, kterou můžete zahrnout do aplikace [!INCLUDE[csprcs](../../includes/csprcs-md.md)] a zveřejnit jako objekt modelu COM, viz [příklad třídy com](https://msdn.microsoft.com/library/6504dea9-ad1c-4993-a794-830fec5270af).

 **Generovat sestavení serializace** Určuje, zda kompilátor použije XML Serializer Generator Tool (Sgen. exe) k vytvoření sestavení serializace XML. Sestavení serializace mohou zlepšit výkon při spuštění <xref:System.Xml.Serialization.XmlSerializer>, pokud jste tuto třídu použili k serializaci typů ve vašem kódu. Ve výchozím nastavení je tato možnost nastavena na hodnotu **auto**, která určuje, že sestavení serializace budou generována pouze v případě, že jste použili <xref:System.Xml.Serialization.XmlSerializer> ke kódování typů v kódu do XML. **Off** určuje, že sestavení serializace nikdy nebyla vygenerována bez ohledu na to, zda váš kód používá <xref:System.Xml.Serialization.XmlSerializer>. **V** určuje, zda mají být sestavení serializace vždy vygenerována. Sestavení serializace jsou pojmenovány `TypeName`. XmlSerializers. dll. Další informace najdete v tématu [XML Serializer Generator Tool (Sgen. exe)](https://msdn.microsoft.com/library/cc1d1f1c-fb26-4be9-885a-3fe84c81cec6).

 **Rozšířené možnosti** Kliknutím zobrazíte dialogové okno [Upřesnit nastavení sestaveníC#()](../../ide/reference/advanced-build-settings-dialog-box-csharp.md) .

## <a name="see-also"></a>Viz také
 [Vlastnosti projektu – odkazy](../../ide/reference/project-properties-reference.md) [ C# na možnosti kompilátoru](https://msdn.microsoft.com/library/d3403556-1816-4546-a782-e8223a772e44)
