---
title: Automatické použití klíčů Product Key
description: Naučte se programově používat kód Product Key při nasazování Visual Studio.
ms.date: 09/24/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: a78da89d8e8ce4251bc9288270628bfe784eca7a
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307711"
---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Automatické použití kódů Product Key při nasazení sady Visual Studio

Kód Product Key můžete použít programově jako součást skriptu, který slouží k automatizaci nasazení Visual Studio. Kód Product Key můžete na zařízení nastavit programově během instalace Visual Studio nebo po dokončení instalace.

::: moniker range=">=vs-2022"

> [!IMPORTANT]
> Visual Studio 2022 je aktuálně ve verzi Preview a během období Visual Studio 2022 je k dispozici v rámci zkušební licence, která nevyžaduje použití klíče Product Key.

::: moniker-end

::: moniker range="vs-2017"

## <a name="apply-the-license-after-installation"></a>Použití licence po instalaci

Nainstalovanou verzi aplikace můžete aktivovat Visual Studio kódem Product Key pomocí nástroje na cílových počítačích `StorePID.exe` v bezobslužném režimu. `StorePID.exe` je utility program, který se instaluje s Visual Studio 2017 v následujícím výchozím umístění:

```shell
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE
```

 Spusťte `StorePID.exe` s vyššími oprávněními, a to buď pomocí agenta System Center, nebo pomocí příkazového řádku se zvýšenými oprávněními. Použijte kód Product Key a kód Microsoft Product Code (MPC).

>[!IMPORTANT]
> Nezapomeňte do kód Product Key zahrnout pomlčky.

 ```shell
 StorePID.exe [product key including the dashes] [MPC]
 ```

::: moniker-end

::: moniker range="vs-2019"

## <a name="apply-the-license-after-installation"></a>Použití licence po instalaci

Nainstalovanou verzi aplikace můžete aktivovat Visual Studio kódem Product Key pomocí nástroje na cílových počítačích `StorePID.exe` v bezobslužném režimu. `StorePID.exe` je utility program, který se instaluje s Visual Studio 2019 v následujícím výchozím umístění:

```shell
C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE
```

 Spusťte `StorePID.exe` s vyššími oprávněními, a to buď pomocí agenta System Center, nebo pomocí příkazového řádku se zvýšenými oprávněními. Použijte kód Product Key a kód Microsoft Product Code (MPC).

>[!IMPORTANT]
> Nezapomeňte do kód Product Key zahrnout pomlčky.

 ```shell
 StorePID.exe [product key including the dashes] [MPC]
 ```

::: moniker-end

::: moniker range="vs-2017"

Následující příklad ukazuje příkazový řádek pro použití licence pro Visual Studio 2017 Enterprise, který má MPC 08860, kód Product Key a předpokládá výchozí umístění `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE` instalace:

```shell
"C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
```

::: moniker-end

::: moniker range="vs-2019"

Následující příklad ukazuje příkazový řádek pro použití licence pro Visual Studio 2019 Enterprise, který má kód MPC 09260, kód Product Key a předpokládá výchozí umístění `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE` instalace:

```shell
"C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 09260
```

::: moniker-end

::: moniker range="vs-2017"

 Následující tabulka uvádí kódy MPC pro každou edici Visual Studio:

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

::: moniker range="vs-2017"

Pokud `StorePID.exe` kód Product Key úspěšně použijete, vrátí hodnotu `%ERRORLEVEL%` 0. Pokud dojde k chybám, vrátí v závislosti na chybovém stavu jeden z následujících kódů:

| Chyba                     | Kód |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

> [!NOTE]
> Když spustíte virtuální instanci Visual Studio, ujistěte se, že jste také virtualizovali místní složku AppData a registr. Pokud chcete řešit potíže s virtuálními instancemi, spusťte `<Visual Studio installation directory>\Common7\IDE\DDConfigCA.exe` příkaz .  

::: moniker-end

::: moniker range="vs-2019"

Pokud `StorePID.exe` kód Product Key úspěšně použijete, vrátí hodnotu `%ERRORLEVEL%` 0. Pokud dojde k chybám, vrátí v závislosti na chybovém stavu jeden z následujících kódů:

| Chyba                     | Kód |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

> [!NOTE]
> Když spustíte virtuální instanci Visual Studio, ujistěte se, že jste také virtualizovali místní složku AppData a registr. Pokud chcete řešit potíže s virtuálními instancemi, spusťte `<Visual Studio installation directory>\Common7\IDE\DDConfigCA.exe` příkaz .  

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Instalace sady Visual Studio](../install/install-visual-studio.md)
* [Vytvoření offline instalace sady Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)