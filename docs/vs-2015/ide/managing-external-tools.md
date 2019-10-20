---
title: Správa externích nástrojů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- Create GUID tool
- RC (Resource Compiler)
- ReBase tool
- Windows NT Message Compiler
- Windows NT C++ Symbol Undecorator
- tstcon32.exe
- Type Library Generator
- Windows NT Image Binder
- tools [Visual Studio], external
- RowsetViewer tool
- utilities, external tools
- Local Test Manager
- OLE DB Rowset Viewer
- Midlc (IDL Compiler)
- ATL Trace Tool
- Odbcte32w.exe
- IDL Compiler
- HCW (Help Workshop)
- Message Compiler [Visual Studio]
- UUID Generator
- MIDL, external tools
- ErrLook tool
- MAKEHM tool
- Error lookup tool
- OLEVIEW (Object Viewer)
- Uuidgen.exe
- WebDbg tool
- OLE/COM Object Viewer
- LTM (Local Test Manager)
- ATLTraceTool.exe
- Bind tool
- Vsvars32.bat
- external tools [Visual Studio]
- ODBC Test
- Windows NT Image Rebaser
- undname.exe
- Vcspawn.exe
- ActiveX Control Test Container
- mc (Message Compiler)
- GUIDGEN tool
- Odbcte32.exe
- DisableMsg tool
- MkTypLib tool
- Help Workshop
- Resource Compiler
ms.assetid: f382fd40-a98f-4934-8c9a-5aeae881acde
caps.latest.revision: 41
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7a9ebda81f013f42aeac23c9c0a8cc5a0a41f5f0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651341"
---
# <a name="managing-external-tools"></a>Správa externích nástrojů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Externí nástroje je možné volat v rámci aplikace Visual Studio. V nabídce **nástroje** je dostupných několik výchozích nástrojů, ale můžete přidat i další vlastní spustitelné soubory.

## <a name="tools-available-on-the-visual-studio-tools-menu"></a>Nástroje, které jsou k dispozici v nabídce Nástroje aplikace Visual Studio
 Následující nástroje můžete volat z nabídky **nástroje** v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Můžete je také volat podle názvu z okna **Snadné spuštění** . Například pro volání nástroje GuidGen. exe zadejte příkaz **Create GUID**.

1. Create GUID: vytvoří identifikátor GUID.

2. Chyba vyhledávání: na základě zadané hodnoty dostane chybovou zprávu. Další informace najdete v tématu [ERRLOOK reference](https://msdn.microsoft.com/library/6040ffc1-2355-4a45-8998-84cbcba4ca91).

3. Trasovací nástroj ATL/MFC: ve zdrojích ATL a MFC zobrazí zprávy trasování ladění.

4. Reverzní Protection – Dotfuscator: chrání programy .NET proti zpětné analýze.

5. SPY++: zobrazí procesy, vlákna, okna a zprávy okna graficky.

6. Editor konfigurace služby WCF: umožňuje vytvářet a upravovat nastavení konfigurace služeb WCF.

> [!WARNING]
> V závislosti na nainstalované verzi aplikace Visual Studio a na použitém nastavení profilu je možné vidět odlišný seznam externích nástrojů. Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="adding-new-tools"></a>Přidání nových nástrojů
 Můžete přidat externí nástroj do nabídky **nástroje** . Otevřete dialogové okno **externí nástroje** a klikněte na tlačítko **Přidat**a zadejte informace do pole informace. Následující položka například způsobí otevření programu Průzkumník Windows v adresáři souboru aktuálně otevřeného v aplikaci Visual Studio:

1. Název: Otevřít umístění souboru

2. Příkaz: explorer.exe

3. Argumenty: /root, "$(ItemDir)"

## <a name="arguments-for-external-tools"></a>Argumenty pro externí nástroje
 Následující argumenty jsou proměnné aplikace Visual Studio, které jsou přiřazeny při spuštění externího nástroje. Odkazy na externí nástroje, jako je Poznámkový blok nebo Spy + +, mohou být uvedeny v nabídce **nástroje** pomocí dialogového okna Externí nástroje.

> [!NOTE]
> Stavový řádek IDE zobrazuje pro označení místa bodu vložení v aktivním editoru kódu proměnné Current Line a Current Column. Proměnná Current Text vrací text nebo kód vybraný v rámci tohoto místa.

|Name|Argument|Popis|
|----------|--------------|-----------------|
|Cesta položky|$(ItemPath)|Celý název souboru aktuálního souboru (jednotka + cesta + název souboru).|
|Adresář položky|$(ItemDir)|Adresář aktuálního souboru (jednotka + cesta).|
|Název souboru položky|$(ItemFilename)|Název aktuálního souboru (název souboru).|
|Přípona položky|$(ItemExt)|Název přípony aktuálního souboru.|
|Aktuální řádek|$(CurLine)|Pozice aktuálního řádku v kurzoru v okně kódu.|
|Aktuální sloupec|$(CurCol)|Pozice aktuálního sloupce v kurzoru v okně kódu.|
|Aktuální text|$(CurText)|Vybraný text.|
|Cílová cesta|$(TargetPath)|Úplný název souboru položky, která má být sestavena (jednotka + cesta + název souboru).|
|Cílový adresář|$(TargetDir)|Adresář položky, která má být sestavena.|
|Cílový název|$(TargetName)|Název souboru položky, která má být sestavena.|
|Cílová Přípona|$(TargetExt)|Přípona názvu souboru položky, která má být sestavena.|
|Binární složka|$(BinDir)|Konečné umístění binárního souboru, který má být sestaven (definované jako jednotka + cesta). Například: **\\. ..\My Documents\Visual Studio \<Version > \\ < ProjectName \> \bin\debug**|
|Adresář projektu|$(ProjDir)|Adresář aktuálního projektu (jednotka + cesta).|
|Název souboru projektu|$(ProjFileName)|Název souboru aktuálního projektu (jednotka + cesta + název souboru).|
|Adresář řešení|$(SolutionDir)|Adresář aktuálního řešení (jednotka + cesta).|
|Název souboru řešení|$(SolutionFileName)|Název souboru aktuálního řešení (jednotka + cesta + název souboru).|

## <a name="see-also"></a>Viz také
 [Nástroje sestavení C/C++](https://msdn.microsoft.com/library/48d9daf4-6bbf-473a-8ce2-bf2923b69f80)
