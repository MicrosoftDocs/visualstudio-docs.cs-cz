---
title: Použití nástroje Emulator Express ke spouštění a ladění cloudové služby Azure v místním počítači | Dokumentace Microsoftu
description: Použití nástroje Emulator Express ke spouštění a ladění cloudové služby na místním počítači
author: mikejo5000
manager: douge
ms.assetid: 73108f98-a552-4817-b7a1-551367b71906
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 03/06/2017
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: 28dd59e3d691df0199afffe93d68d60668c6afe4
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2018
ms.locfileid: "51003172"
---
# <a name="using-emulator-express-to-run-and-debug-an-azure-cloud-service-on-a-local-machine"></a>Spuštění a ladění cloudové služby Azure na místním počítači pomocí expresního emulátoru
Podle použití nástroje Emulator Express, může testování a ladění cloudovou službu bez spuštění sady Visual Studio jako správce. Můžete nastavit nastavení projektu pro použití Emulator Express nebo úplný emulátor, v závislosti na požadavcích vaší cloudové služby. Další informace o úplný emulátor, naleznete v tématu [spuštění aplikace Azure v emulátoru Compute](/azure/storage/common/storage-use-emulator).

## <a name="using-emulator-express-in-visual-studio"></a>Pomocí expresní emulátor v sadě Visual Studio
Při vytvoření projektu Azure v Azure SDK 2.3 nebo novější Emulator Express je automaticky používá. Pro existující projekty, které byly vytvořeny ve starší verzi sady Azure SDK pomocí následujících kroků vyberte Emulator Express:

1. Vytvořte nebo otevřete v sadě Visual Studio projekt cloudové služby Azure.

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a v místní nabídce vyberte **vlastnosti**.

1. Na stránkách vlastností projektů, vyberte **webové** kartu.

    ![Vlastnosti projektu cloudové služby Azure](./media/vs-azure-tools-emulator-express-debug-run/web-properties.png)

1. V části **místní vývojový Server**vyberte **možnosti použít službu IIS Express**.

1. V části **emulátor**vyberte **použít expresní emulátor**.
   
1. Pokud chcete spustit expresní emulátor, spusťte následující příkaz z příkazového řádku: 

    ```
    csrun.exe /useemulatorexpress
    ```

## <a name="emulator-express-limitations"></a>Emulator Express omezení
Omezení nástroje Emulator Express jsou známy následující problémy: 

- Emulator Express je nekompatibilní s Webový Server služby IIS.
- Cloudové služby může obsahovat více rolí, ale je omezený na jednu instanci každé role.
- Čísla portů pod 1 000, nelze přistupovat. Pokud používáte zprostředkovatele ověřování, které obvykle využívá port pod 1 000, potřebujete změnit tuto hodnotu na číslo portu, který je uveden výše 1 000.
- Žádná omezení, které se vztahují k emulátoru Azure Compute platí také pro Emulator Express. Například nemůžete mít více než 50 instancí role jedno nasazení. Další informace o emulátoru Azure Compute, naleznete v tématu [spuštění aplikace Azure v emulátoru Compute](http://go.microsoft.com/fwlink/p/?LinkId=623050).

## <a name="next-steps"></a>Další kroky
[Ladění cloudové služby Azure](https://msdn.microsoft.com/library/azure/ee405479.aspx)
