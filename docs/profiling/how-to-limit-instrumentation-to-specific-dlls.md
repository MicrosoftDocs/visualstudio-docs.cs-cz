---
title: 'Postupy: omezení instrumentace na konkrétní knihovny DLL | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, runtime profiling control window
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aefa0d5953d1e8d61615ac5bfe0af136082c96f3
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2018
ms.locfileid: "34843946"
---
# <a name="how-to-limit-instrumentation-to-specific-dlls"></a>Postupy: omezení instrumentace na konkrétní knihovny DLL

Pomocí metody profilování instrumentace můžete omezit shromažďování profilování dat na jeden nebo více knihovny DLL v aplikaci. Profilu jeden nebo více knihovny DLL v aplikaci, vytvořte relaci výkonu, která zahrnuje. *dll* soubory jako cíle. Můžete zadat knihovny DLL, které chcete profil jako projekty v řešení sady Visual Studio nebo jako nezávislé binární soubory.

## <a name="to-limit-instrumentation-to-specific-dlls-in-a-visual-studio-solution"></a>K omezení instrumentace na konkrétní knihovny DLL v řešení sady Visual Studio

1. Otevřete řešení, která obsahuje knihovnu DLL v sadě Visual Studio.

2. Na **analyzovat** nabídce vyberte možnost **spusťte Průvodce výkonu**.

3. Zvolte **instrumentace** jako profilování metodu a pak klikněte na tlačítko **Další**.

4. Z **který z následujících dostupných cílů chcete profil?**, vyberte název. *knihovny DLL* projektu a pak klikněte na **Další**.

5. Klikněte na tlačítko **Dokončit** k ukončit průvodce a zobrazení v nové relaci výkonu **prohlížeč výkonu** okno.

6. Klikněte pravým tlačítkem na **cíle** a pak vyberte **přidat cílový projekt**.

7. Z **přidat cílový projekt** vyberte spustitelný projekt, který chcete použít k prověření knihovnu DLL.

     Volitelné. Všechny projekty knihovny DLL, které chcete, můžete přidat do profilu.

8. Pokud chcete zabránit shromažďování dat pro projektu přidané, klikněte pravým tlačítkem na název projektu a potom zrušte **nástrojem** zaškrtávací políčko.

## <a name="to-specify-specific-dlls-to-profile-as-independent-binaries"></a>Chcete-li určit konkrétní knihovny DLL do profilu jako nezávislé binárních souborů

1. Otevřete Visual Studio.

2. Na **analyzovat** nabídce vyberte možnost **spusťte Průvodce výkonu**.

3. Z **který z následujících dostupných cílů chcete profil**, vyberte **profilu dynamické knihovny (. Knihovny DLL)** a pak klikněte na **Další**.

4. Na druhé stránce průvodce proveďte následující kroky:

    - Zadejte název a cesta k souboru. *dll* soubor, který chcete profil v **cesta Dll**. Můžete také kliknutím na tlačítko se třemi tečkami (...) a soubor vyhledejte v **knihovny DLL do profilu** dialogové okno. Všimněte si, že je nutné zadat kopii. *dll* soubor, který bude spuštěn spustitelný soubor (. *exe*) souboru, který jste vybrali další.

    - Zadejte název a cesta k souboru ke spustitelnému souboru (. *exe*) soubor, který bude. *dll* v **cesta ke spustitelnému souboru**. Můžete také kliknutím na tlačítko se třemi tečkami (...) a soubor vyhledejte v **spustitelný soubor spusťte** dialogové okno.

    - Volitelné. Zadejte všechny argumenty příkazového řádku, které chcete předat spustitelný soubor ve **argumenty příkazového řádku**. V případě potřeby zadejte pracovní adresář pro aplikaci v **pracovní adresář**.

    - Klikněte na tlačítko **Další**.

5. Zvolte **instrumentace** jako profilování metodu a pak klikněte na tlačítko **Další**.

6. Klikněte na tlačítko **Dokončit** k ukončit průvodce a zobrazení v nové relaci výkonu **prohlížeč výkonu** okno.

7. Volitelné. Chcete-li přidat další. *dll* soubory, klikněte pravým tlačítkem na **cíle** a pak vyberte **přidat cíl binární**. Vyberte soubory z **přidat cíl binární** dialogové okno.

    > [!NOTE]
    > Nezadávejte spustitelný soubor (. *exe*) soubor, který vykonává knihovny DLL.

## <a name="see-also"></a>Viz také:

[Řízení shromažďování dat](../profiling/controlling-data-collection.md)  
[Postupy: Omezení instrumentace na konkrétní funkce](../profiling/how-to-limit-instrumentation-to-specific-functions.md)