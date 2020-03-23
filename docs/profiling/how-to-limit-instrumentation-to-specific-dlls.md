---
title: 'Postup: Omezit instrumentaci na konkrétní knihovny DLL | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, runtime profiling control window
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 066262a3fae35e82904b011165813e9dd75d9987
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778814"
---
# <a name="how-to-limit-instrumentation-to-specific-dlls"></a>Postupy: Omezení instrumentace na konkrétní knihovny DLL

Pomocí metody instrumentace profilování můžete omezit shromažďování dat profilování na jednu nebo více knihoven DLL v aplikaci. Chcete-li profilovat jeden nebo více knihoven DLL v aplikaci, vytvořte relaci výkonu, která obsahuje . *dll* jako cíle. Můžete určit knihovny DLL, které chcete profilovat jako projekty v řešení sady Visual Studio nebo jako nezávislé binární soubory.

## <a name="to-limit-instrumentation-to-specific-dlls-in-a-visual-studio-solution"></a>Omezení instrumentace na konkrétní knihovny DLL v řešení sady Visual Studio

1. Otevřete řešení, které obsahuje dll v sadě Visual Studio.

2. V nabídce **Analyzovat** vyberte **Průvodce spuštěním výkonu**.

3. Jako metodu profilování zvolte **Instrumentace** a klepněte na tlačítko **Další**.

4. V části **Který z následujících dostupných cílů chcete profilovat?** *dll* projektu a klepněte na tlačítko **Další**.

5. Klepnutím na **tlačítko Dokončit** ukončete průvodce a zobrazte novou relaci výkonu v okně **Průzkumník výkonu.**

6. Klikněte pravým tlačítkem myši na **cíle** a pak vyberte **Přidat cílový projekt**.

7. Ze seznamu **Přidat cílový projekt** vyberte spustitelný projekt, který chcete použít k výkonu dll.

     Nepovinný parametr. Můžete přidat všechny projekty DLL, které chcete profilovat.

8. Chcete-li zabránit shromažďování dat pro přidaný projekt, klikněte pravým tlačítkem myši na název projektu a zrušte zaškrtnutí **políčka Nástroj.**

## <a name="to-specify-specific-dlls-to-profile-as-independent-binaries"></a>Určení konkrétních knihoven DLL pro profil ování jako nezávislých binárních souborů

1. Otevřete sadu Visual Studio.

2. V nabídce **Analyzovat** vyberte **Průvodce spuštěním výkonu**.

3. V části **Který z následujících dostupných cílů chcete profilovat**, vyberte **profil ovou knihovnu dynamických odkazů (. DLL)** a potom klepněte na tlačítko **Další**.

4. Na druhé stránce průvodce proveďte následující kroky:

    - Zadejte cestu a název souboru . *DLL,* který chcete profilovat v **cestě dll**. Můžete také klepnout na tlačítko se třemi tečkami (...) a najít soubor v **knihovně dynamických odkazů do** dialogového okna profilu. Všimněte si, že je nutné zadat kopii . *dll,* který bude spuštěn spustitelným souborem (.* exe*) který vyberete jako další.

    - Zadejte cestu a název souboru spustitelného souboru (.* exe*) soubor, který bude vykonávat . *dll* v **cestě spustitelného souboru**. Můžete také klepnout na tlačítko se třemi tečkami (...) a najít soubor v **dialogovém okně Spustitelný soubor ke spuštění.**

    - Nepovinný parametr. Zadejte všechny argumenty příkazového řádku, které chcete předat spustitelnému souboru, do **argumentů příkazového řádku**. V případě potřeby zadejte pracovní adresář pro aplikaci v **pracovním adresáři**.

    - Klikněte na **Další**.

5. Jako metodu profilování zvolte **Instrumentace** a klepněte na tlačítko **Další**.

6. Klepnutím na **tlačítko Dokončit** ukončete průvodce a zobrazte novou relaci výkonu v okně **Průzkumník výkonu.**

7. Nepovinný parametr. Chcete-li přidat další . *dll,* klepněte pravým tlačítkem myši na **cíle** a pak vyberte **přidat cílový binární soubor**. Vyberte soubory z dialogového okna **Přidat cílový binární.**

    > [!NOTE]
    > Nezadávejte spustitelný soubor (.* exe*) soubor, který vykonává DLL.

## <a name="see-also"></a>Viz také

[Řízení sběru](../profiling/controlling-data-collection.md)
dat[Jak omezit instrumentaci na konkrétní funkce](../profiling/how-to-limit-instrumentation-to-specific-functions.md)
