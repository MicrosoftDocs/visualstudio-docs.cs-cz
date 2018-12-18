---
title: Intellitrace data
ms.date: 10/13/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliTrace, configuring test settings
- Diagnostic Data Adapter, InteliTrace
- debugging [Visual Studio ALM], difficult issues using IntelliTrace
- Test Runner, InteliTrace
ms.assetid: 02b6716f-569e-4961-938a-e790a0c74b5c
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: cad52f39fc45e5561e2a87f12c804cb0d445d96a
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064754"
---
# <a name="how-to-collect-intellitrace-data-to-help-debug-difficult-issues"></a>Postupy: shromažďování dat IntelliTrace pro ladění složitých problémů

Můžete nakonfigurovat adaptér diagnostických dat pro technologii IntelliTrace lze shromažďovat informace o specifickém diagnostickém trasování v Visual Stdio. Testy mohou tento adaptér používat. Test může shromažďovat podstatné diagnostické události aplikace, které může vývojář později použít pro trasování skrze kód a nalezení příčiny chyby. Adaptér diagnostiky dat pro technologii IntelliTrace lze použít pro manuální, nebo automatizované testy.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Technologie IntelliTrace pracuje pouze v aplikaci, která je napsána ve spravovaném kódu. Pokud testujete webovou aplikaci, která jako klienta používá prohlížeč, neměli byste povolit IntelliTrace pro klienta v nastavení testu protože není k dispozici pro trasovacího žádný spravovaný kód. V takovém případě můžete nastavit prostředí a shromažďovat IntelliTrace data vzdáleně na webovém serveru.

IntelliTrace data jsou uložena v souboru, který má příponu *.iTrace*. Při spuštění testu a testovací krok nezdaří, můžete vytvořit chybu. Soubor IntelliTrace, který obsahuje diagnostické informace, je automaticky připojen k této chybě.

> [!NOTE]
> Adaptér diagnostiky dat pro technologii IntelliTrace nevytvoří soubor IntelliTrace, pokud test proběhne úspěšně. Soubor se uloží pouze při selhání testovacího případu nebo při odeslání hlášení o chybě.

Data shromažďovaná do souboru IntelliTrace zvyšují efektivitu ladění zkrácením doby potřebné k reprodukci a diagnostice chyby v kódu. Navíc vzhledem k tomu, že soubor IntelliTrace lze sdílet s jinou osobou, která může replikovat místní relaci ve svém počítači, se snižuje pravděpodobnost, že chyby nebudou reprodukovatelné.

> [!NOTE]
> Pokud v nastaveních testů povolíte technologii IntelliTrace, nebude fungovat shromažďování dat o pokrytí kódu.

> [!WARNING]
> Adaptér diagnostiky dat pro technologii IntelliTrace funguje díky instrumentaci spravovaného procesu, která musí být provedena po načtení testů pro testovací běh. Pokud již byl proces, který chcete sledovat, spuštěn, nebudou shromážděny žádné soubory IntelliTrace, protože proces již probíhá. To lze obejít ověřením, že se proces před načtením testů ukončil. Poté po načtení testů nebo spuštění prvního testu spusťte proces.

Následující postup popisuje, jak nakonfigurovat data IntelliTrace, která chcete shromažďovat. Tento postup platí pro editor konfigurace v nástroji Microsoft Test Manager a nastavení testu dialogové okno v sadě Visual Studio.

> [!NOTE]
> Uživatelský účet pro testovacího agenta, který je používán k shromažďování dat IntelliTrace, musí být členem skupiny administrátorů. Další informace najdete v tématu [instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).

## <a name="configure-the-data-to-collect-with-the-intellitrace-diagnostic-data-adapter"></a>Konfigurace dat pro shromažďování dat prostřednictvím adaptéru diagnostiky dat technologie IntelliTrace

Před provedením kroků v tomto postupu je nutné otevřít nastavení testu pomocí nástroje Microsoft Test Manager nebo Visual Studio a vyberte **dat a diagnostiky** stránky.

### <a name="to-configure-the-data-to-collect-with-the-intellitrace-diagnostic-data-adapter"></a>Konfigurace dat pro shromažďování dat prostřednictvím adaptéru diagnostiky dat technologie IntelliTrace

1.  Vyberte roli, kterou chcete použít pro shromažďování dat IntelliTrace.

2.  Vyberte **IntelliTrace**.

3.  Pokud přidáváte IntelliTrace pro roli webového klienta nebo pro webovou aplikaci ASP.NET, je také nutné vybrat **ASP.NET Client Proxy pro IntelliTrace a dopad testu**.

     Tento server proxy umožňuje shromažďovat informace o voláních http z klienta na webový server pro adaptéry diagnostických dat IntelliTrace a dopad testu.

    > [!WARNING]
    > Pokud se rozhodnete použít vlastní účet pro identitu, která je používána pro fond aplikací na serveru služby IIS, kde máte v úmyslu shromažďovat data Intellitrace, je třeba vytvořit místní profil uživatele v počítači služby IIS pro vlastní účet, který je používán. Místní profil lze pro vlastní účet vytvořit jednorázovým přihlášením na počítači se službou IIS místně, nebo spuštěním následujícího příkazu příkazového řádku pomocí vlastních pověření účtu:
    >
    > **runas /user:domain\name /profile cmd.exe**

4.  Zvolte **konfigurovat** pro **IntelliTrace** upravit výchozí nastavení technologie IntelliTrace.

     Zobrazí se dialogové okno pro konfiguraci dat, která budou shromažďována.

    > [!WARNING]
    > Pokud povolíte shromažďování dat IntelliTrace, nebude fungovat shromažďování dat pokrytí kódu.

5.  Zvolte **Obecné** kartu. Vyberte **pouze události IntelliTrace** Chcete-li zaznamenávat podstatné diagnostické události, které mají minimální dopad na výkon při testování.

     -nebo-

     Vyberte **události IntelliTrace a informací o volání** pro záznam diagnostických událostí a metoda úroveň trasování, které ukazuje informace o volání. Tato úroveň trasování může mít vliv na výkon při spuštění testů.

6.  Chcete-li shromažďovat data z vaší aplikace technologie ASP.NET, na kterém běží na serveru služby IIS, vyberte **shromažďovat data z aplikací ASP.NET, které jsou spuštěny na serveru služby IIS**. Nastavte a nakonfigurujte testovacího agenta v roli webového serveru. Zobrazit [instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).

7.  Zvolte **moduly** kartu. Vyberte buď **shromažďování dat ze všech modulů kromě následujících** a používat **přidat** pro přidání do seznamu modulů a **odebrat** pro odebrání modulu. Tato volba umožňuje zahrnout všechny moduly, které jsou spuštěny v systému kromě modulů, jež zadáte.

     -nebo-

     Vyberte **shromažďovat data z pouze modulů** a používat **přidat** pro přidání do seznamu modulů a **odebrat** pro odebrání modulu. Tato volba umožňuje přesně určit požadované moduly.

    > [!NOTE]
    > Pokud je to možné, vyberte konkrétní postupy, které chcete sledovat. To je doporučeno pro optimální výkon.

8.  Zvolte **procesy** kartu. Vyberte **shromažďování dat ze všech procesů kromě následujících** a používat **přidat** pro přidání do seznamu procesů a **odebrat** pro odebrání procesu. Tato volba umožňuje zahrnout všechny procesy, které jsou spuštěny v systému kromě procesů, jež zadáte.

     -nebo-

     Vyberte **shromažďovat data pouze z konkrétních procesů** a používat **přidat** pro přidání do seznamu procesů a **odebrat** pro odebrání procesu. Tato volba umožňuje přesně určit požadované procesy.

9. (Volitelné) Zvolte **události IntelliTrace** kartu. Zaškrtněte nebo zrušte zaškrtnutí jednotlivých kategorií událostí IntelliTrace, které chcete zahrnout nebo vyloučit při shromažďování diagnostických událostí.

10. (Volitelné) Rozbalte každou kategorii událostí IntelliTrace a zaškrtněte nebo zrušte zaškrtnutí každé konkrétní události, kterou chcete zahrnout nebo vyloučit v událostech IntelliTrace.

11. (Volitelné) Zvolte **Upřesnit** kartu. V dalším kroku vyberte šipku vedle položky **maximální množství místa na disku pro záznam** a vyberte maximální velikost, kterou chcete pro tento soubor IntelliTrace povolit.

    > [!NOTE]
    > Pokud velikost pro záznam zvětšíte, může dojít k problému s vypršením času při ukládání tohoto záznamu společně s výsledky testů.

12. Pokud používáte Microsoft Test Manager, zvolte **Uložit**. Pokud používáte Visual Studio, zvolte **OK**. Nastavení technologie IntelliTrace je nyní nakonfigurováno a uloženo pro nastavení testů.

    > [!NOTE]
    > Chcete-li obnovit konfiguraci adaptéru diagnostických dat, zvolte **obnovit výchozí konfiguraci** pro sadu Visual Studio nebo **obnovit výchozí** nástroje Microsoft Test Manager.

## <a name="see-also"></a>Viz také:

- [Shromažďování diagnostických dat při testování (Azure testovací plány)](/azure/devops/test/collect-diagnostic-data?view=vsts)
- [Shromažďování diagnostických dat v manuálních testů (Azure testovací plány)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)
- [Shromažďování diagnostických údajů pomocí nastavení testů](../test/collect-diagnostic-information-using-test-settings.md)
- [Shromažďování dat IntelliTrace](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)