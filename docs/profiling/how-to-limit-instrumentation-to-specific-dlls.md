---
title: 'Postupy: omezení instrumentace na konkrétní knihovny DLL | Microsoft Docs'
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778814"
---
# <a name="how-to-limit-instrumentation-to-specific-dlls"></a>Postupy: omezení instrumentace na konkrétní knihovny DLL

Pomocí metody profilace instrumentace můžete omezit shromažďování dat profilování na jednu nebo více knihoven DLL v aplikaci. Chcete-li profilovat jednu nebo více knihoven DLL v aplikaci, vytvořte relaci výkonu, která zahrnuje. soubory *DLL* jako cíle. Můžete určit knihovny DLL, které chcete profilovat jako projekty v řešení aplikace Visual Studio nebo jako nezávislé binární soubory.

## <a name="to-limit-instrumentation-to-specific-dlls-in-a-visual-studio-solution"></a>Omezení instrumentace na konkrétní knihovny DLL v řešení sady Visual Studio

1. Otevřete řešení, které obsahuje knihovnu DLL v aplikaci Visual Studio.

2. V nabídce **analyzovat** vyberte možnost **Spustit Průvodce výkonem**.

3. Jako metodu profilace zvolte **instrumentace** a pak klikněte na **Další**.

4. Z **toho, který z následujících dostupných cílů chcete profilovat?** vyberte název. projekt *knihovny DLL* a potom klikněte na tlačítko **Další**.

5. Kliknutím na tlačítko **Dokončit** ukončíte průvodce a zobrazíte novou relaci výkonu v okně **prohlížeč výkonu** .

6. Klikněte pravým tlačítkem na **cíle** a pak vyberte **Přidat cílový projekt**.

7. V seznamu **Přidat cílový projekt** vyberte spustitelný projekt, který chcete použít pro cvičení knihovny DLL.

     Volitelné. Můžete přidat všechny projekty knihoven DLL, které chcete profilovat.

8. Chcete-li zabránit shromažďování dat pro přidaný projekt, klikněte pravým tlačítkem myši na název projektu a poté zrušte zaškrtnutí políčka **instrumentace** .

## <a name="to-specify-specific-dlls-to-profile-as-independent-binaries"></a>Určení specifických knihoven DLL pro profilování jako nezávislých binárních souborů

1. Otevřete Visual Studio.

2. V nabídce **analyzovat** vyberte možnost **Spustit Průvodce výkonem**.

3. Z **toho, který z následujících dostupných cílů byste chtěli profilovat**, vyberte **profil knihovny DLL (. DLL)** a poté klikněte na tlačítko **Další**.

4. Na druhé stránce průvodce proveďte následující kroky:

    - Zadejte cestu a název souboru. soubor *DLL* , který chcete profilovat v **cestě knihovny DLL**. Můžete také kliknout na tlačítko se třemi tečkami (...) a vyhledat soubor v dialogovém okně **Knihovna dynamického propojení do profilu** . Všimněte si, že je nutné zadat kopii. soubor *DLL* , který bude spuštěn spustitelným souborem (. *soubor exe*), který vyberete další.

    - Zadejte cestu a název souboru spustitelného souboru (. *exe*), který bude vyvolávat. *Knihovna DLL* v **cestě ke spustitelnému souboru**. Můžete také kliknout na tlačítko se třemi tečkami (...) a vyhledat soubor v dialogovém okně **spustitelného souboru, který se má spustit** .

    - Volitelné. Zadejte argumenty příkazového řádku, které chcete předat spustitelnému souboru v **argumentech příkazového řádku**. V případě potřeby zadejte pracovní adresář pro aplikaci v **pracovním adresáři**.

    - Klikněte na tlačítko **Další**.

5. Jako metodu profilace zvolte **instrumentace** a pak klikněte na **Další**.

6. Kliknutím na tlačítko **Dokončit** ukončíte průvodce a zobrazíte novou relaci výkonu v okně **prohlížeč výkonu** .

7. Volitelné. Pro přidání dalších. soubory *DLL* , klikněte pravým tlačítkem na **cíle** a pak vyberte **Přidat cílový binární soubor**. Vyberte soubory z dialogového okna **Přidat cílový binární soubor** .

    > [!NOTE]
    > Nezadávejte spustitelný soubor (. *exe*) soubor, který vykonává knihovny DLL.

## <a name="see-also"></a>Viz také:

[Řízení shromažďování dat](../profiling/controlling-data-collection.md)
[Postupy: omezení instrumentace na konkrétní funkce](../profiling/how-to-limit-instrumentation-to-specific-functions.md)
