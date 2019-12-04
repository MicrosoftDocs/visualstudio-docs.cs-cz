---
title: 'Návod: profilace z příkazového řádku s použitím vzorkování | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance tools, command-line tools
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 09272c8cf2dff02d3be024b9c3eeab8b51f56df7
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777969"
---
# <a name="walkthrough-command-line-profiling-using-sampling"></a>Návod: profilace z příkazového řádku s použitím vzorkování

Tento návod ukazuje, jak profilovat aplikaci pomocí nástrojů příkazového řádku a vzorkování k identifikaci problémů s výkonem.

V tomto návodu provedete kroky procesu profilování spravované aplikace pomocí nástrojů příkazového řádku a pomocí vzorkování můžete izolovat a identifikovat problémy s výkonem v aplikaci.

V tomto návodu budete postupovat podle těchto kroků:

- Profilování aplikace pomocí nástrojů příkazového řádku a vzorkování.
- Analyzovat ukázkové výsledky profilace, které hledají a odstraňují problémy s výkonem.

## <a name="prerequisites"></a>Požadavky

- Zprostředkující porozumění [!INCLUDE[csharp_current_short](../misc/includes/csharp_current_short_md.md)]
- Zprostředkující porozumění práci s nástroji příkazového řádku
- Kopie [ukázky PeopleTrax –](performance-explorer.md)
- Chcete-li pracovat s informacemi poskytnutými profilací, je vhodné mít k dispozici informace o symbolech ladění.

## <a name="command-line-profiling-using-the-sampling-method"></a>Profilace z příkazového řádku pomocí metody vzorkování

Vzorkování je metoda profilace, pomocí které se pravidelně dotazuje konkrétní proces, aby se zjistila aktivní funkce. Výsledná data poskytují počet, jak často byla funkce nad zásobníkem volání při vzorkování procesu.

> [!NOTE]
> Postup získání cesty k nástrojům pro profilaci najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na 64 počítačích jsou k dispozici i 64 32 a 32bitové verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, je nutné přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo je přidat do samotného příkazu.

### <a name="to-profile-the-peopletrax-application-by-using-the-sampling-method"></a>Profilování aplikace PeopleTrax – pomocí metody vzorkování

1. Nainstalujte ukázkovou aplikaci PeopleTrax – a sestavte prodejní verzi aplikace.

2. Otevřete okno příkazového řádku a přidejte Nástroje pro profilaci adresář do proměnné prostředí místní cesta.

3. Změňte pracovní adresář na adresář, který obsahuje binární soubory PeopleTrax –.

4. Zadejte následující příkaz pro nastavení příslušných proměnných prostředí:

    ```cmd
    VSPerfCLREnv /sampleon
    ```

5. Spusťte profilaci spuštěním *VSPerfCmd. exe*, což je nástroj příkazového řádku, který řídí Profiler. Následující příkaz spustí aplikaci a Profiler v režimu vzorkování:

    ```cmd
    VsPerfCmd /start:sample /output:PeopleTraxReport.vsp /launch:PeopleTrax.exe
    ```

     Spustí se proces profileru a připojí se k procesu *PeopleTrax –. exe* . Proces profileru začne zapisovat shromážděná data profilování do souboru sestavy.

6. Klikněte na **získat lidi**.

7. Klikněte na **ExportData**.

     Poznámkový blok otevře a zobrazí nový soubor, který obsahuje exportovaná data z **PeopleTrax –** .

8. Zavřete Poznámkový blok a pak zavřete aplikaci **PeopleTrax –** .

9. Vypněte profiler. Zadejte následující příkaz:

    ```cmd
    VSPerfCmd /shutdown
    ```

10. K resetování proměnných prostředí použijte následující příkaz:

    ```cmd
    VSPerfCLREnv /sampleoff
    ```

11. Data profilování jsou uložena v. soubor *VSP* analyzuje výsledky pomocí jedné z následujících metod:

    - Otevřete. soubor *VSP* v integrovaném vývojovém prostředí sady Visual Studio.

         ani

    - Vygeneruje hodnotu oddělenou čárkou (. *CSV*) soubor pomocí nástroje příkazového řádku *VSPerfReport. exe*. Chcete-li generovat sestavy pro použití mimo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrované vývojové prostředí, použijte následující příkaz:

        ```cmd
        VSPerfReport <dir> PeopleTraxReport.vsp /output:<dir> /summary:all
        ```

## <a name="see-also"></a>Viz také:

[Přehled výkonnostní relace](../profiling/performance-session-overview.md)
[profil z příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md)
[VSPerfCmd](../profiling/vsperfcmd.md)
[porozumění hodnotám dat vzorkování](../profiling/understanding-sampling-data-values.md)
[zobrazení sestav výkonu](../profiling/performance-report-views.md)
