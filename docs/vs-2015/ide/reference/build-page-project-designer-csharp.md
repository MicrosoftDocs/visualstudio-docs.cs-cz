---
title: Stránka sestavení, Návrhář projektu (C#) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cs.ProjectPropertiesBuild
helpviewer_keywords:
- Build options [C#]
- Project Designer, Build page
ms.assetid: 77ff1bfc-d633-4634-ba29-9afdb6d7e362
caps.latest.revision: 47
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a377db0ac82b672d053e59c621714945fa9b515c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49837176"
---
# <a name="build-page-project-designer-c"></a>Stránka Sestavení, návrhář projektu (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Použití **sestavení** stránku **Návrháře projektu** k určení vlastností konfigurace sestavení projektu. Tato stránka se vztahuje na [!INCLUDE[csprcs](../../includes/csprcs-md.md)] pouze pro projekty.  
  
 Pro přístup k **sestavení** zvolte uzel projektu (ne **řešení** uzlu) v **Průzkumníka řešení**. Klikněte na tlačítko **projektu**, **vlastnosti** na řádku nabídek. Jakmile se zobrazí Návrhář projektu, klikněte na tlačítko **sestavení** kartu.  
  
 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]  
  
## <a name="configuration-and-platform"></a>Konfigurace a platforma  
 Tyto možnosti umožňují vybrat konfigurace a platformy k zobrazení a úpravě.  
  
> [!NOTE]
>  Pomocí zjednodušených konfigurací sestavení systém projektu určuje, jestli se má sestavení ladění nebo vydání verze. Proto nejsou tyto možnosti zobrazeny. Další informace najdete v tématu [konfigurace ladění a verzí projektu](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
 **Konfigurace**  
 Určuje které nastavení konfigurace má být zobrazeno nebo upraveno. Toto nastavení může být **aktivní (ladění)** (Toto je výchozí), **ladění**, **vydání**, nebo **všechny konfigurace**.  
  
 **Platforma**  
 Určuje které nastavení platformy má být zobrazeno nebo upraveno. Ve výchozím nastavení **aktivní (jakýkoli procesor)**. Můžete změnit aktivní platformu pomocí **nástroje Configuration Manager**. Další informace najdete v tématu [postupy: vytvoření a úprava konfigurací](../../ide/how-to-create-and-edit-configurations.md).  
  
## <a name="general"></a>Obecné  
 Tyto možnosti umožňují konfigurovat několik nastavení kompilátoru jazyka C#.  
  
 **Symboly podmíněné kompilace**  
 Určuje symboly, s nimiž se má provést Podmíněná kompilace. Symboly oddělte středníkem (";"). Další informace najdete v tématu [/ define (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/f17d7b4d-82d0-4133-8563-68cced1cac6e).  
  
 **Definovat konstantu DEBUG**  
 Definuje DEBUG jako symbol ve všech souborů zdrojového kódu ve vaší aplikaci. Tento výběr je ekvivalentní k použití `/define:DEBUG` možnost příkazového řádku.  
  
 **Definovat konstantu TRACE**  
 Definuje TRACE jako symbol ve všech souborů zdrojového kódu ve vaší aplikaci. Tento výběr je ekvivalentní k použití `/define:TRACE` možnost příkazového řádku.  
  
 **Cíl CPU**  
 Určuje procesor, který bude cílen výstupním souborem. Zvolte **x86** jakýkoli procesor kompatibilní s verzí Intel 32-bit, zvolte **x64** jakýkoli procesor kompatibilní s verzí Intel 64-bit, zvolte **ARM** pro procesory ARM, nebo zvolte  **Jakýkoli procesor** k určení, že je přijatelný jakýkoli procesor. **Jakýkoli procesor** je výchozí hodnota pro projekty, protože umožňuje aplikaci, aby běžela v nejširší škále hardwaru.  
  
 Další informace najdete v tématu [/Platform (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/c290ff5e-47f4-4a85-9bb3-9c2525b0be04).  
  
 **Preferovat 32 bitů**  
 Pokud **preferovat 32bitovou verzi** zaškrtávací políčko zaškrtnuto, aplikace běží jako 32bitová aplikace ve 32bitové a 64bitové verze Windows. Pokud políčko není zaškrtnuto, aplikace běží jako 32bitová aplikace ve 32bitové verze Windows a jako na 64bitovými verzemi Windows 64-bit aplikace.  
  
 Pokud spustíte aplikaci jako 64bitovou aplikaci, zdvojnásobí se velikost ukazatele, a může dojít k problémům kompatibilita s ostatními knihovnami, které jsou výhradně 32bitové. Je vhodné spouštět 64bitovou aplikaci pouze v případě, že potřebuje více než 4 GB paměti nebo 64bitové instrukce poskytují významné výkonnostní zlepšení.  
  
 Toto zaškrtávací políčko je dostupné jenom v případě, že jsou splněny všechny následující podmínky:  
  
- Na **sestavit stránku**, **Cílová platforma** seznamu je nastavena na **jakýkoli procesor**.  
  
- Na **stránky aplikace**, **typ výstupu** seznam určuje, že projekt je aplikace.  
  
- Na **stránky aplikace**, **Cílová architektura** seznamu určuje rozhraní .NET Framework 4.5.  
  
  **Povolit nezabezpečený kód**  
  Umožňuje kód, který se používá [nebezpečné](http://msdn.microsoft.com/library/7e818009-1c6e-4b9e-b769-3728a01586a0) ke kompilaci klíčové slovo. Další informace najdete v tématu [/ unsafe (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/fdb77ed9-da03-45bd-bb7f-250704da1bcc).  
  
  **Optimalizovat kód**  
  Povolí nebo zakáže optimalizace provedené kompilátorem za účelem zkontrolujte výstupní soubor menší, rychlejší a efektivnější. Další informace najdete v tématu [/ optimize (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0).  
  
## <a name="errors-and-warnings"></a>Chyby a upozornění  
 Následující nastavení se používají ke konfiguraci chyby a upozornění možnosti procesu sestavení.  
  
 **Úroveň upozornění**  
 Upřesňuje úroveň zobrazení upozornění kompilátoru. Další informace najdete v tématu [/ warn (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/5f80ff59-4991-4382-9f9a-77da18446e71).  
  
 **Potlačení upozornění**  
 Blokuje možnost kompilátoru generovat jedno nebo více upozornění. Více čísel upozornění oddělte čárkou nebo středníkem. Další informace najdete v tématu [/nowarn (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4).  
  
## <a name="treat-warnings-as-errors"></a>Zpracovávat upozornění jako chyby  
 Tato nastavení slouží k určení, která upozornění jsou považována za chyby. Vyberte jednu z následujících možností pro označení podmínek pro vrácení chyby, když sestavení narazí na upozornění. Další informace najdete v tématu [/warnaserror (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).  
  
 **None**  
 Nezpracovává žádná upozornění jako chyby.  
  
 **Specifická upozornění**  
 Zachází s určenými varováními jako s chybami. Více čísel upozornění oddělte čárkou nebo středníkem.  
  
 **Všechny**  
 Zpracuje všechna upozornění jako chyby.  
  
## <a name="output"></a>Výstup  
 Následující nastavení se používají ke konfiguraci možností výstupu pro proces sestavení.  
  
 **Výstupní cesta**  
 Určuje umístění výstupních souborů pro tuto konfiguraci projektu. Zadejte cestu k výstupu sestavení v tomto poli, nebo zvolte **Procházet** tlačítko a zadejte cestu. Všimněte si, že cesta je relativní; Pokud zadáte absolutní cestu, bude uložena jako relativní. Výchozí cesta je bin\Debug nebo bin\Release\\. Další informace najdete v tématu [konfigurace ladění a verzí projektu](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
 Pomocí zjednodušených konfigurací sestavení systém projektu určuje, jestli se má sestavení ladění nebo vydání verze. **Sestavení** příkaz **ladění** nabídky (F5) vloží sestavení do místa ladění bez ohledu na to **výstupní cesta** zadáte. Ale **sestavení** příkaz **sestavení** nabídky se vloží do umístění, které zadáte. Další informace najdete v tématu [konfigurace ladění a verzí projektu](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
 **Soubor dokumentace XML**  
 Určuje název souboru, do které dokumentace se zpracuje komentáře. Další informace najdete v tématu [/DOC (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/849eea59-c936-4311-bad8-d07404480f2a).  
  
 **Zaregistrovat pro interoperabilitu COM**  
 Označuje, že bude vaše spravovaná aplikace vystavovat objekt modelu COM (Obálka volatelná aplikacemi COM) umožňující objektu modelu COM interakci s vaší spravovanou aplikací. **Typ výstupu** vlastnost [stránky aplikace](../../ide/reference/application-page-project-designer-visual-basic.md) z **Návrháře projektu** pro tuto aplikaci musí být nastaven na hodnotu **knihovny tříd** v pořadí **zaregistrovat pro interoperabilitu COM** vlastnost k dispozici. Příklad třídy, které můžete zahrnout do vaší [!INCLUDE[csprcs](../../includes/csprcs-md.md)] aplikace a použít jako objekt modelu COM naleznete v tématu [Ukázka třídy COM](http://msdn.microsoft.com/library/6504dea9-ad1c-4993-a794-830fec5270af).  
  
 **Generovat sestavení serializace**  
 Určuje, zda kompilátor použije nástroj generátoru Serializéru XML (Sgen.exe) k tvorbě XML serializace sestavení. Sestavení serializace mohou zvýšit výkon při spuštění <xref:System.Xml.Serialization.XmlSerializer> Pokud jste již použili k serializaci typů ve vašem kódu. Ve výchozím nastavení je tato možnost nastavená na **automaticky**, která určuje, že se serializace sestavení vytvoří pouze v případě, že jste už použili <xref:System.Xml.Serialization.XmlSerializer> ke kódování typů ve vašem kódu pro XML. **Vypnout** Určuje, že sestavení serializace nebudou nikdy generována, bez ohledu na to, jestli váš kód používá <xref:System.Xml.Serialization.XmlSerializer>. **Na** Určuje, že sestavení serializace budou vždy generována. Jsou pojmenované sestavení serializace `TypeName`. XmlSerializers.dll. Další informace najdete v tématu [nástroj XML Serializer Generator (Sgen.exe)](http://msdn.microsoft.com/library/cc1d1f1c-fb26-4be9-885a-3fe84c81cec6).  
  
 **Pokročilé**  
 Kliknutím zobrazíte [pokročilé vytváření dialogové okno nastavení (C#)](../../ide/reference/advanced-build-settings-dialog-box-csharp.md) dialogové okno.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace k vlastnostem projektu](../../ide/reference/project-properties-reference.md)   
 [Možnosti kompilátoru jazyka C#](http://msdn.microsoft.com/library/d3403556-1816-4546-a782-e8223a772e44)



