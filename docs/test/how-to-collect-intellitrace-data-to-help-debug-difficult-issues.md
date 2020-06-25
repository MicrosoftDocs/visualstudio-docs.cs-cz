---
title: IntelliTrace data
ms.date: 10/13/2016
ms.topic: how-to
helpviewer_keywords:
- IntelliTrace, configuring test settings
- Diagnostic Data Adapter, InteliTrace
- debugging [Visual Studio ALM], difficult issues using IntelliTrace
- Test Runner, InteliTrace
ms.assetid: 02b6716f-569e-4961-938a-e790a0c74b5c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d0983967d42c6daa89b9a690b93fb97872e98603
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85288252"
---
# <a name="how-to-collect-intellitrace-data-to-help-debug-difficult-issues"></a>Postupy: shromáždění dat IntelliTrace, která vám pomůžou ladit obtížné problémy

Adaptér diagnostických dat pro IntelliTrace můžete nakonfigurovat tak, aby shromáždil konkrétní informace trasování diagnostiky v aplikaci Visual Studio. Testy mohou tento adaptér používat. Test může shromažďovat podstatné diagnostické události aplikace, které může vývojář později použít pro trasování skrze kód a nalezení příčiny chyby. Adaptér diagnostiky dat pro technologii IntelliTrace lze použít pro manuální, nebo automatizované testy.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Technologie IntelliTrace pracuje pouze v aplikaci, která je napsána ve spravovaném kódu. Pokud testujete webovou aplikaci, která používá prohlížeč jako klienta, neměli byste povolit IntelliTrace pro klienta v nastavení testu, protože není k dispozici žádný spravovaný kód pro trasování. V takovém případě můžete chtít nastavit prostředí a shromažďovat data IntelliTrace vzdáleně na webovém serveru.

Data IntelliTrace se ukládají do souboru s příponou *. iTrace*. Když spustíte test a testovací krok neproběhne úspěšně, můžete vytvořit chybu. Soubor IntelliTrace, který obsahuje diagnostické informace, je automaticky připojen k této chybě.

> [!NOTE]
> Adaptér diagnostiky dat pro technologii IntelliTrace nevytvoří soubor IntelliTrace, pokud test proběhne úspěšně. Soubor se uloží pouze při selhání testovacího případu nebo při odeslání hlášení o chybě.

Data shromažďovaná do souboru IntelliTrace zvyšují efektivitu ladění zkrácením doby potřebné k reprodukci a diagnostice chyby v kódu. Navíc vzhledem k tomu, že soubor IntelliTrace lze sdílet s jinou osobou, která může replikovat místní relaci ve svém počítači, se snižuje pravděpodobnost, že chyby nebudou reprodukovatelné.

> [!NOTE]
> Pokud v nastaveních testů povolíte technologii IntelliTrace, nebude fungovat shromažďování dat o pokrytí kódu.

> [!WARNING]
> Adaptér diagnostiky dat pro technologii IntelliTrace funguje díky instrumentaci spravovaného procesu, která musí být provedena po načtení testů pro testovací běh. Pokud již byl proces, který chcete sledovat, spuštěn, nebudou shromážděny žádné soubory IntelliTrace, protože proces již probíhá. To lze obejít ověřením, že se proces před načtením testů ukončil. Poté po načtení testů nebo spuštění prvního testu spusťte proces.

::: moniker range="vs-2017"
Následující postup popisuje, jak nakonfigurovat data IntelliTrace, která chcete shromažďovat. Tento postup platí pro editor konfigurace v dialogovém okně Microsoft Test Manager a nastavení testu v aplikaci Visual Studio.
::: moniker-end
::: moniker range=">=vs-2019"
Následující postup popisuje, jak nakonfigurovat data IntelliTrace, která chcete shromažďovat. Tyto kroky platí pro dialogové okno nastavení testu v aplikaci Visual Studio.
::: moniker-end

> [!NOTE]
> Uživatelský účet pro testovacího agenta, který je používán k shromažďování dat IntelliTrace, musí být členem skupiny administrátorů. Další informace najdete v tématu [instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).

## <a name="configure-the-data-to-collect-with-the-intellitrace-diagnostic-data-adapter"></a>Nakonfigurujte data, která se mají shromáždit pomocí adaptéru diagnostických dat IntelliTrace.

::: moniker range="vs-2017"
Před provedením kroků v tomto postupu je nutné otevřít nastavení testu z buď Microsoft Test Manager, nebo sady Visual Studio a vybrat stránku **data a diagnostika** .
::: moniker-end
::: moniker range=">=vs-2019"
Před provedením kroků v tomto postupu je nutné otevřít nastavení testu ze sady Visual Studio a vybrat stránku **data a diagnostika** .
::: moniker-end

### <a name="to-configure-the-data-to-collect-with-the-intellitrace-diagnostic-data-adapter"></a>Konfigurace dat, která se mají shromáždit pomocí adaptéru diagnostických dat IntelliTrace

1. Vyberte roli, kterou chcete použít pro shromažďování dat IntelliTrace.

2. Vyberte **IntelliTrace**.

3. Pokud přidáváte IntelliTrace pro roli webového klienta nebo pro webovou aplikaci ASP.NET, musíte také vybrat **ASP.NET Client proxy pro IntelliTrace a dopad testu**.

     Tento proxy server umožňuje shromažďovat informace o voláních http z klienta na webový server pro adaptéry diagnostických dat IntelliTrace a test vlivu.

    > [!WARNING]
    > Pokud se rozhodnete použít vlastní účet pro identitu, která se používá pro fond aplikací na serveru služby IIS (Internet Information Server), ve kterém chcete shromažďovat data IntelliTrace, musíte pro vlastní účet, který se používá, vytvořit místní profil uživatele na počítači IIS. Místní profil lze pro vlastní účet vytvořit jednorázovým přihlášením na počítači se službou IIS místně, nebo spuštěním následujícího příkazu příkazového řádku pomocí vlastních pověření účtu:
    >
    > **runas/user: doména \ název \/Profile cmd.exe**

4. Pokud chcete upravit výchozí nastavení IntelliTrace, vyberte **Konfigurovat** pro **IntelliTrace** .

     Zobrazí se dialogové okno pro konfiguraci dat, která budou shromažďována.

    > [!WARNING]
    > Pokud povolíte shromažďování dat IntelliTrace, nebude fungovat shromažďování dat pokrytí kódu.

5. Klikněte na kartu **Obecné** . Vyberte **události IntelliTrace pouze** pro záznam významných diagnostických událostí, které mají minimální dopad na výkon při testování.

     -nebo-

     Vyberte **události IntelliTrace a zavolejte informace** pro záznam diagnostických událostí a trasování na úrovni metod, které zobrazuje informace o volání. Tato úroveň trasování může mít vliv na výkon při spuštění testů.

6. Pokud chcete shromažďovat data z aplikace ASP.NET, která běží na Internetová informační služba, vyberte **shromažďovat data z aplikací ASP.NET, které běží na Internetová informační služba**. Nastavte a nakonfigurujte testovacího agenta na roli webového serveru. Viz [instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).

7. Zvolte kartu **moduly** . Vyberte buď možnost **shromáždit data ze všech modulů s výjimkou následujících možností** a pomocí možnosti **Přidat** přidejte do seznamu moduly a **odeberte** modul. Tato volba umožňuje zahrnout všechny moduly, které jsou spuštěny v systému kromě modulů, jež zadáte.

     -nebo-

     Vyberte možnost **shromažďovat data pouze z následujících modulů** a použijte příkaz **Přidat** pro přidání do seznamu modulů a příkaz **Remove** pro odebrání modulu. Tato volba umožňuje přesně určit požadované moduly.

    > [!NOTE]
    > Pokud je to možné, vyberte konkrétní postupy, které chcete sledovat. To je doporučeno pro optimální výkon.

8. Zvolte kartu **procesy** . Vyberte možnost **shromažďovat data ze všech procesů kromě následujících** a použijte příkaz **Přidat** pro přidání do seznamu procesů a **Odebrat** pro odebrání procesu. Tato volba umožňuje zahrnout všechny procesy, které jsou spuštěny v systému kromě procesů, jež zadáte.

     -nebo-

     Vyberte možnost **shromažďovat data pouze z určených procesů** a pomocí ovládacího panelu **Přidat** přidejte do seznamu procesů a **odeberte** proces odebrání. Tato volba umožňuje přesně určit požadované procesy.

9. Volitelné Zvolte kartu **události IntelliTrace** . zaškrtněte nebo zrušte zaškrtnutí každé kategorie události IntelliTrace, kterou chcete zahrnout nebo vyloučit při shromažďování diagnostických událostí.

10. (Volitelné) Rozbalte každou kategorii událostí IntelliTrace a zaškrtněte nebo zrušte zaškrtnutí každé konkrétní události, kterou chcete zahrnout nebo vyloučit v událostech IntelliTrace.

11. Volitelné Vyberte kartu **Upřesnit** . Potom zvolte šipku vedle **maximálního místa na disku pro záznam** a vyberte maximální velikost, kterou chcete povolit, aby soubor IntelliTrace mohl použít.

    > [!NOTE]
    > Pokud velikost pro záznam zvětšíte, může dojít k problému s vypršením času při ukládání tohoto záznamu společně s výsledky testů.

12. Pokud používáte Microsoft Test Manager (zastaralé v aplikaci Visual Studio 2017), klikněte na tlačítko **Uložit**. Pokud používáte aplikaci Visual Studio, klikněte na **tlačítko OK**. Nastavení technologie IntelliTrace je nyní nakonfigurováno a uloženo pro nastavení testů.

    ::: moniker range="vs-2017"
    > [!NOTE]
    > Chcete-li obnovit konfiguraci pro tento adaptér diagnostických dat, vyberte možnost **obnovit na výchozí konfiguraci** pro aplikaci Visual Studio nebo **nastavte výchozí nastavení** pro Microsoft Test Manager.
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    > [!NOTE]
    > Chcete-li obnovit konfiguraci pro tento adaptér diagnostických dat, vyberte možnost **obnovit na výchozí konfiguraci** v aplikaci Visual Studio.
    ::: moniker-end

## <a name="see-also"></a>Viz také

- [Shromažďovat diagnostická data při testování (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts)
- [Shromažďovat diagnostická data v ručních testech (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)
- [Shromažďování diagnostických informací pomocí nastavení testu](../test/collect-diagnostic-information-using-test-settings.md)
- [Shromažďování dat IntelliTrace](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)
