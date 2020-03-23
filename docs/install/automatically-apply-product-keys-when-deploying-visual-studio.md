---
title: Automatické použití kódů Product Key
description: Přečtěte si, jak programově použít kódy Product Key při nasazení sady Visual Studio.
ms.date: 09/24/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: e7f331536de264186bc2977cc4acaaab02147e13
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115215"
---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Automatické použití kódů Product Key při nasazení sady Visual Studio

Kód Product Key můžete použít programově jako součást skriptu, který se používá k automatizaci nasazení sady Visual Studio. Kód Product Key můžete nastavit na zařízení programově buď během instalace sady Visual Studio, nebo po dokončení instalace.

## <a name="apply-the-license-after-installation"></a>Použití licence po instalaci

::: moniker range="vs-2017"

Nainstalovanou verzi sady Visual Studio s kódem `StorePID.exe` Product Key můžete aktivovat pomocí nástroje na cílových počítačích v tichém režimu. `StorePID.exe`je nástroj, který se instaluje pomocí sady Visual Studio 2017 v následujícím výchozím umístění: <br> `C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE`

::: moniker-end

::: moniker range="vs-2019"

Nainstalovanou verzi sady Visual Studio s kódem `StorePID.exe` Product Key můžete aktivovat pomocí nástroje na cílových počítačích v tichém režimu. `StorePID.exe`je nástroj, který se instaluje pomocí sady Visual Studio 2019 v následujícím výchozím umístění: <br> `C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE`

::: moniker-end

 Spouštět `StorePID.exe` se zvýšenými oprávněními, buď pomocí agenta System Center nebo příkazového řádku se zvýšenými oprávněními. Postupujte podle kódu Product Key a kódu produktu společnosti Microsoft (MPC).

>[!IMPORTANT]
> Nezapomeňte do kódu Product Key zahrnout pomlčky.

 ```cmd
 StorePID.exe [product key including the dashes] [MPC]
 ```

::: moniker range="vs-2017"

Následující příklad ukazuje příkazový řádek pro použití licence pro Visual Studio 2017 Enterprise, který má MPC 08860, kód Product Key aplikace `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE`a předpokládá výchozí umístění instalace:

```cmd
"C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
```

::: moniker-end

::: moniker range="vs-2019"

Následující příklad ukazuje příkazový řádek pro použití licence pro Visual Studio 2019 Enterprise, který má MPC 09260, kód Product Key z `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE`, a předpokládá výchozí umístění instalace:

```cmd
"C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 09260
```

::: moniker-end

::: moniker range="vs-2017"

 V následující tabulce jsou uvedeny kódy MPC pro každé vydání sady Visual Studio:

| Visual Studio Edition                | Mpc   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2017        | 08860 |
| Visual Studio Professional 2017      | 08862 |
| Visual Studio Test Professional 2017 | 08866 |

::: moniker-end

::: moniker range="vs-2019"

| Visual Studio Edition                | Mpc   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2019        | 09260 |
| Visual Studio Professional 2019      | 09262 |

::: moniker-end

Pokud `StorePID.exe` úspěšně použije kód Product Key, `%ERRORLEVEL%` vrátí hodnotu 0. Pokud dojde k chybám, vrátí jeden z následujících kódů v závislosti na chybovém stavu:

| Chyba                     | kód |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

> [!NOTE]
> Při spuštění virtuální instance sady Visual Studio, ujistěte se, že také virtualizovat místní AppData složky a registru. Chcete-li odstranit potíže `C:\Program Files (x86)\Microsoft Visual Studio\<version>\Common7\IDE\DDConfigCA.exe`s virtuálními instancemi, spusťte program .  

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Instalace sady Visual Studio](../install/install-visual-studio.md)
* [Vytvoření offline instalace sady Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)
