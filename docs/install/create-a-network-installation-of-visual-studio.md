---
title: Vytvoření síťové instalace
description: Zjistěte, jak vytvořit bod instalace sítě pro nasazení sady Visual Studio v rámci organizace.
ms.date: 10/17/2017
ms.technology: vs-acquisition
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 4CABFD20-962E-482C-8A76-E4012052F701
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cb259e1b6b90b93d01cdabd5622e0397d037c250
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159448"
---
# <a name="create-a-network-installation-of-visual-studio-2017"></a>Vytvoření síťové instalace sady Visual Studio 2017

Obvykle správce podnikové sítě vytvoří bod instalace sítě pro nasazení do klientských pracovních stanic. Jsme navrhli tak Visual Studio 2017 umožňuje soubory pro počáteční instalaci spolu se všechny aktualizace produktů do jedné složky do mezipaměti. (Tento proces se také označuje jako _vytvoření rozložení platného pro_.) Jsme udělali to tak, aby pracovní stanice klienta můžete používat stejné umístění v síti ke správě jejich instalace i v případě, že ještě neprovedli aktualizaci na nejnovější servisní aktualizace.

 > [!NOTE]
 > Pokud máte víc edicí sady Visual Studio používá v rámci vaší organizace (například Visual Studio Professional i Visual Studio Enterprise), musíte vytvořit sdílenou složku instalace samostatné sítě pro jednotlivé edice.

## <a name="download-the-visual-studio-bootstrapper"></a>Stažení zaváděcího nástroje Visual Studio

**Stáhněte si** edici sady Visual Studio, které chcete. Ujistěte se, že klikněte na tlačítko **Uložit**a potom klikněte na tlačítko **otevřít složku**.

Nastavení spustitelných&mdash;nebo na konkrétnější, soubor zaváděcí nástroj&mdash;by měl odpovídat jedné z následujících akcí.

|Edice | Stáhnout|
|-------------|-----------------------|
|Visual Studio Enterprise | [**vs_enterprise.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2017) |
|Visual Studio Professional | [**vs_professional.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2017) |
|Visual Studio Community | [**vs_community.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2017) |

Zahrnout další podporované bootstrapperů [vs_buildtools.exe](https://aka.ms/vs/15/release/vs_buildtools.exe), [vs_feedbackclient.exe](https://aka.ms/vs/15/release/vs_feedbackclient.exe), [vs_teamexplorer.exe](https://aka.ms/vs/15/release/vs_teamexplorer.exe), [vs_testagent.exe](https://aka.ms/vs/15/release/vs_testagent.exe), [vs_testcontroller.exe](https://aka.ms/vs/15/release/vs_testcontroller.exe), a [vs_testprofessional.exe](https://aka.ms/vs/15/release/vs_testprofessional.exe).

## <a name="create-an-offline-installation-folder"></a>Vytvořte složku offline instalace

Musíte mít internetové připojení k dokončení tohoto kroku. K vytvoření offline instalace jazykům a všechny funkce, použijte jeden z příkazů z následujících příkladů.

   > [!IMPORTANT]
   > Úplné rozložení sady Visual Studio 2017 vyžaduje minimálně 35 GB místa na disku a může trvat nějakou dobu ke stažení.  Zobrazit [přizpůsobení rozložení sítě](#customizing-the-network-layout) podrobné informace o tom, jak vytvořit rozložení s jenom ty komponenty, kterou chcete nainstalovat.
   >
   > [!TIP]
   > Ujistěte se, spusťte příkaz z adresáře ke stažení. Obvykle to `C:\Users\<username>\Downloads` v počítači se systémem Windows 10.

- Pro Visual Studio Enterprise spusťte:

  ```vs_enterprise.exe --layout c:\vs2017offline```

- Pro sadu Visual Studio Professional spusťte:

  ```vs_professional.exe --layout c:\vs2017offline```

- Pro Visual Studio Community spusťte:

  ```vs_community.exe --layout c:\vs2017offline```

## <a name="modify-the-responsejson-file"></a>Upravte soubor response.json

Můžete upravit response.json nastavit výchozí hodnoty, které se používají, když se spustí instalační program.  Například můžete nakonfigurovat `response.json` souboru vybrat konkrétní sadu úloh vybrat automaticky.
Zobrazit [instalace automatizace sady Visual Studio souborem odpovědí](automated-installation-with-response-file.md) podrobnosti.

## <a name="copy-the-layout-to-a-network-share"></a>Rozložení kopírovat do síťové sdílené složky

Hostování rozložení do sdílené síťové složky, aby ji můžete spustit z jiné počítače.
* Příklad:<br>
```xcopy /e c:\vs2017offline \\server\products\VS2017```

## <a name="customizing-the-network-layout"></a>Přizpůsobení rozložení sítě

Existuje několik možností, které lze použít k přizpůsobení rozvržení sítě. Lze vytvořit částečné rozložení obsahující jenom určitou sadu [národní prostředí](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales), [úlohy, komponenty a jejich doporučená nebo volitelné závislosti](workload-and-component-ids.md). To může být užitečné, pokud víte, že se chystáte nasadit jenom určité podmnožiny úlohy na klientských pracovních stanic. Typické parametry příkazového řádku pro přizpůsobení rozložení patří:

* ```--add``` Chcete-li určit [ID úlohy nebo komponenty](workload-and-component-ids.md).  Pokud `--add` se používá, pouze úlohy a komponenty zadaným `--add` se stáhnou.  Pokud `--add` se nepoužívá, všechny úlohy a komponenty staženy.
* ```--includeRecommended``` Chcete-li zahrnout všechny součásti, které jsou doporučené pro zadané ID úlohy
* ```--includeOptional``` Chcete-li zahrnout všechny doporučené a volitelné součásti pro zadané ID úlohy.
* ```--lang``` Chcete-li určit [národní prostředí](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales).

Tady je několik příkladů toho, jak vytvořit vlastní částečné rozložení.

* Pokud chcete stáhnout všechny úlohy a komponenty pouze pro jeden jazyk, spusťte: <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US```
* Pokud chcete stáhnout všechny úlohy a komponenty pro různé jazyky, spusťte: <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US de-DE ja-JP```
* Chcete-li stáhnout jednu úlohu pro všechny jazyky, spusťte <br> ```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --includeRecommended```
* Ke stažení dvou úloh a volitelnou součástí tři jazyky, spusťte: <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended --lang en-US de-DE ja-JP ```
* Pokud chcete stáhnout dvě úlohy a všech jejich doporučených součástí, spusťte: <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended ```
* Chcete-li stáhnout dvě úlohy a všechny jejich doporučené a volitelné součásti, spusťte: <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeOptional ```

### <a name="new-in-153"></a>Novinka v 15.3

Při spuštění příkazu rozložení se uloží možnosti, které zadáte (třeba úlohy a jazyky). Rozložení následné příkazy bude obsahovat všechny předchozí možnosti.  Tady je příklad rozložení se sadou jeden pro angličtinu pouze:

```vs_enterprise.exe --layout c:\VS2017Layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US```

Pokud chcete aktualizovat tento rozložení na novější verzi, není nutné specifikovat žádné další parametry příkazového řádku. Předchozí nastavení jsou uloženy a používány všechny následné rozložení příkazy v této složce rozložení.  Následující příkaz aktualizuje existující částečné rozložení.

```vs_enterprise.exe --layout c:\VS2017Layout```

Pokud chcete přidat další úlohy, tady příklad toho, jak to provést. V tomto případě přidáme sady funkcí Azure a lokalizovaný jazyk.  Teď Managed Desktop i Azure jsou zahrnuté v tomto rozvržení.  Jazykové prostředky anglické a německé zahrnout pro všechny tyto úlohy. Rozložení se aktualizuje na nejnovější dostupnou verzi.

```vs_enterprise.exe --layout c:\VS2017Layout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE```

Pokud chcete aktualizovat existující rozložení na úplné rozložení, použijte--všechny možnosti, jak je znázorněno v následujícím příkladu.

```vs_enterprise.exe --layout c:\VS2017Layout --all```

## <a name="deploying-from-a-network-installation"></a>Nasazení z instalace v síti

Správci můžou nasadit sady Visual Studio na klientských pracovních stanic, jako součást instalačního skriptu. Nebo uživatelé, kteří mají oprávnění správce, můžete spustit instalační program přímo ze sdílené složky pro instalaci sady Visual Studio na svém počítači.

- Uživatelé mohou nainstalovat spuštěním: <br>```\\server\products\VS2017\vs_enterprise.exe```
- Správce můžete nainstalovat v bezobslužném režimu spuštěním: <br>```\\server\products\VS2017\vs_enterprise.exe --quiet --wait --norestart```

> [!TIP]
> Při spuštění jako součást dávkového souboru, `--wait` možnost zajišťuje, že `vs_enterprise.exe` proces čeká na dokončení instalace je dříve, než vrátí ukončovací kód. To je užitečné, pokud chce správce podnikové sítě provádět další akce instalace byla dokončena (například [použít kód product key pro úspěšnou instalaci](automatically-apply-product-keys-when-deploying-visual-studio.md)) ale musí počkat na dokončení zpracování instalace Návratový kód z této instalace.  Pokud nepoužijete `--wait`, `vs_enterprise.exe` proces ukončí před dokončením instalace a vrátí nesprávné ukončovací kód, který nepředstavuje stavu operace instalace.

Při instalaci z rozložení, je obsah, který je nainstalován získaných z rozložení. Ale pokud vyberete součást, která se nenachází v rozložení, ji bude možné získat z Internetu.  Pokud chcete zabránit ve stahování veškerý obsah, který nebyl nalezen v rozložení, použijte instalační program sady Visual Studio `--noWeb` možnost.  Pokud `--noWeb` se používá a rozložení chybí veškerý obsah, který je se rozhodli nainstalovat, instalace selže.

### <a name="error-codes"></a>Kódy chyb

Pokud jste použili `--wait` parametr a potom v závislosti na výsledek operace, `%ERRORLEVEL%` proměnnou prostředí je nastavená na jednu z následujících hodnot:

  | **Hodnota** | **výsledek** |
  | --------- | ---------- |
  | 0 | Operace byla úspěšně dokončena |
  | 3010 | Operace byla úspěšně dokončena, ale instalace aktualizace vyžaduje restartování, než je možné |
  | Ostatní | Došlo k selhání podmínku – Další informace v protokolech |

## <a name="updating-a-network-install-layout"></a>Síťový diagram instalace aktualizace

Jakmile budou dostupné aktualizace produktu, můžete chtít [aktualizovat síťový diagram instalace](update-a-network-installation-of-visual-studio.md) začlenit aktualizované balíčky.

## <a name="how-to-create-a-layout-for-a-previous-visual-studio-2017-release"></a>Jak vytvořit rozložení pro předchozí verze sady Visual Studio 2017

> [!NOTE]
> Visual Studio 2017 bootstrapperů, které jsou k dispozici na [visualstudio.microsoft.com](http://visualstudio.microsoft.com) stáhnout a nainstalovat nejnovější verzi sady Visual Studio 2017 k dispozici pokaždé, když se jejich spuštění. Je-li stáhnout zaváděcí nástroj Visual Studio ještě dnes a spustíte ji za šest měsíců od této chvíle, nainstaluje, který je k dispozici v daném čase novější vydání sady Visual Studio 2017. Pokud vytvoříte rozložení, instalace sady Visual Studio z tohoto rozložení nainstaluje konkrétní verzi nástroje Visual Studio, která existuje v rozložení. I když online možná existuje novější verze, získat verzi sady Visual Studio, která je v rozložení.

Pokud je potřeba vytvořit rozložení pro starší verze sady Visual Studio 2017, můžete přejít na https://my.visualstudio.com ke stažení "Pevná" verzích bootstrapperů Visual Studio 2017.

### <a name="how-to-get-support-for-your-offline-installer"></a>Jak získat podporu pro offline instalační program

Pokud dochází k potížím s offline instalací chcete vědět o něm. Nejlepší způsob, jak Řekněte nám, je použít [nahlásit problém](../ide/how-to-report-a-problem-with-visual-studio-2017.md) nástroj. Při použití tohoto nástroje můžete nám odeslat telemetrii a protokoly, musíme pomáhají diagnostikovat a opravit problém.

Nabízíme také [ **živý chat** ](https://visualstudio.microsoft.com/vs/support/#talktous) (jenom v angličtině) možnost podpory pro problémy související s instalací.

Další možnosti podpory dostupné, máme příliš. Seznam najdete v tématu naše [kontaktujte nás](../ide/how-to-report-a-problem-with-visual-studio-2017.md) stránky.

## <a name="see-also"></a>Viz také:

* [Instalace sady Visual Studio](install-visual-studio.md)
* [Příručka pro správce aplikace Visual Studio](visual-studio-administrator-guide.md)
* [Instalace sady Visual Studio s použitím parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
* [ID úloh a komponent sady Visual Studio](workload-and-component-ids.md)
