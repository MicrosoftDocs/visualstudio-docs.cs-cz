---
title: Synchronizace změn mezi XCode a sadou Visual Studio | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c71a4d7c-120e-4559-a114-3a99c4b860a9
ms.technology: vs-ide-mobile
author: corob-msft
ms.author: corob
manager: douge
ms.workload:
- xamarin
ms.openlocfilehash: a32d72869a14e22ba8707036cd4b549ef5228d3b
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/31/2018
ms.locfileid: "39379299"
---
# <a name="sync-changes-between-xcode-and-visual-studio"></a>Synchronizace změn mezi XCode a sadou Visual Studio
Microsoft Visual C++ pro vývoj mobilních řešení pro komponentu zahrnuje vzdálené možnosti pro synchronizaci vaší práce mezi vaším Počítačem a vašeho macu. V kombinaci se počítače s Visual Studio nebo Mac, nové možnosti jsou k dispozici pro iOS projekty aplikací v sadě Visual Studio, můžete použít k otevření projektu v XCode, přesuňte váš kód mezi XCode a sadou Visual Studio a vyčistit dočasný adresář projektu XCode.

 Použití možností vzdálený počítač, váš projekt musí být projekt aplikace pro iOS a sady Visual Studio musí být párována s vašeho macu. Požadavky a pokyny o tom, jak pár Mac najdete v tématu [instalace a konfigurace nástroje potřebné k vytváření pomocí iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).

## <a name="the-remote-machine-menu"></a>V nabídce vzdáleného počítače
 V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt aplikace pro iOS k zobrazení v místní nabídce. Vyberte **vzdálený počítač** položku, kterou chcete zobrazit dostupné možnosti vzdáleného.

 ![Vzdálený počítač položky nabídky v Průzkumníku řešení](../cross-platform/media/cppmdd_u2_remotemachine_menu.jpg "CPPMDD_U2_RemoteMachine_Menu")

 Tyto příkazy umožňují otevřete projekt v XCode, přesouvat místní změny nebo celý projekt mezi Visual Studio a XCode a vyčistit dočasné soubory na vzdáleném počítači.

### <a name="open-in-xcode"></a>Otevřít v Xcodu
 Otevřete projekt v XCode ze sady Visual Studio na **vzdálený počítač** podnabídky, zvolte **otevřít v Xcodu** otevřít zvolený projekt na spárovaném vzdáleném počítači. Vcremote server slouží k XCode na počítači Mac otevřete a přejděte do dočasného adresáře na počítači Mac, který obsahuje kopii projektu vytvoří. Visual Studio se zobrazí dialogové okno zobrazující dočasný adresář pro projekt používá. Akce prováděné na vzdáleném počítači jsou také uvedeny v **výstup** okna v sadě Visual Studio. Neuvidíte, budete muset vybrat **vzdálený počítač Visual C++** v **zobrazit výstup z:** rozevírací seznam v horní části **výstup** okna.

 ![V okně výstupu se zobrazí akce vzdáleného počítače. ](../cross-platform/media/cppmdd_u2_remotemachine_output.png "CPPMDD_U2_RemoteMachine_Output")

 Všechny nástroje XCode na počítači Mac, slouží k úpravě kódu a prostředků, scénářů a akce. V sadě Visual Studio je váš projekt aplikace pro iOS opatřen poznámkou "Otevřít v XCode" k označení, že mohou být provedeny změny ve vzdáleném počítači. Po dokončení úprav můžete stahování ze vzdáleného počítače nebo přírůstkové načítat vzdálené příkazy pro kopírování změn zpět do projektu sady Visual Studio.

### <a name="push-to-remote-and-incremental-push-to-remote"></a>Vložit do vzdálené a přírůstkové nabízení na vzdálený počítač
 Pokud jste provedli změny pro váš projekt aplikace pro iOS v sadě Visual Studio, přírůstkové vložení do vzdálených příkazů a metodou Push do vzdáleného umožňuje přesunout soubory změněné projektu na spárovaném vzdálený počítač. Nasdílení změn do vzdáleného příkazu zkopíruje všechny soubory projektu do vzdáleného počítače. Přírůstkové vložit do vzdáleného příkazu zkopíruje jen změněné soubory na vzdálený počítač. Pro velké projekty s malým změnám přírůstkové příkaz šetří čas a šířky pásma.

 Kopírování souborů projektu do počítače Mac v sadě Visual Studio **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt aplikace pro iOS otevřete místní nabídku. Vyberte **vzdálený počítač** a zvolte buď **nabízet na vzdálený počítač** nebo **přírůstkové nabízet na vzdálený počítač** kopírování souborů projektu v sadě Visual Studio do vašeho macu.

### <a name="pull-from-remote-and-incremental-pull-from-remote"></a>Vyžádání ze vzdáleného a přírůstkové stahování ze vzdáleného počítače
 Po provedení změny do projektu v prostředí XCode přejděte změny zpět do sady Visual Studio pro synchronizaci projektů.

 Zkopírujte soubory projektu z Macu, v sadě Visual Studio **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt aplikace pro iOS otevřete místní nabídku. Vyberte **vzdálený počítač** a zvolte buď **stahovat ze vzdáleného počítače** nebo **přírůstkové stahovat ze vzdáleného počítače** kopírování souborů projektu z počítače Mac se sadou Visual Studio.

### <a name="clean-remote"></a>Vyčistit vzdálený počítač
 Vyčistit vzdálený příkaz slouží k odstranění souborů v adresáři dočasné projektu ve vzdáleném počítači. Obsah adresáře, včetně žádné zdrojové soubory nebo sestavení produkty, odeberou se na vašem počítači Mac. Ujistěte se, že všechny změny, které chcete zachovat zpět do sady Visual Studio s použitím o přijetí změn ze vzdáleného ani přírůstkové přijmout jejich změny ze vzdáleného před použitím příkazu vyčistit vzdálený nebyly synchronizovány.

 Pro čištění adresáře dočasných projektu ve vzdáleném počítači, v sadě Visual Studio **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt aplikace pro iOS otevřete místní nabídku. Vyberte **vzdálený počítač** a zvolte **vyčistit vzdálený** odebrání soubory v adresáři projektu vašeho macu.