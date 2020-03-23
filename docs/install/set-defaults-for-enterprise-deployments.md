---
title: Nastavení výchozích hodnot pro podniková nasazení
description: Přečtěte si o zásadách domény a dalších operacích konfigurace pro podniková nasazení sady Visual Studio.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- gpo
- policy
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9B7B4608-7A3F-4FF4-BDCE-42D9F7CE6DBA
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: d03912eecd7b3cfa3563fc095453fee3ddf9b163
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114291"
---
# <a name="set-defaults-for-enterprise-deployments-of-visual-studio"></a>Nastavení výchozích hodnot pro podniková nasazení sady Visual Studio

Můžete nastavit zásady registru, které ovlivňují nasazení sady Visual Studio. Tyto zásady jsou globální pro nové instalační program a ovlivňují:

- Kde jsou nainstalovány některé balíčky sdílené s jinými verzemi nebo instancemi
- Kde jsou balíčky ukládány do mezipaměti
- Zda jsou všechny balíčky ukládány do mezipaměti

Některé z těchto zásad můžete nastavit pomocí [možností příkazového řádku](use-command-line-parameters-to-install-visual-studio.md), nastavit hodnoty registru v počítači nebo je dokonce distribuovat pomocí zásad skupiny v rámci organizace.

## <a name="registry-keys"></a>Klíče registru

Existuje několik umístění, kde můžete nastavit výchozí hodnoty rozlehlé sítě, chcete-li povolit jejich řízení prostřednictvím zásad skupiny nebo přímo v registru. Visual Studio se postupně dívá, jestli nebyly nastaveny nějaké zásady organizace. jakmile je zjištěna hodnota zásady v pořadí uvedeném, zbývající klíče jsou ignorovány.

1. `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup`
2. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`
3. `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\VisualStudio\Setup`(na 64bitových operačních systémech)

> [!IMPORTANT]
> Pokud `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup` nenastavíte klíč a místo toho nastavíte jeden z dalších klíčů, měli byste nastavit oba ostatní klíče v 64bitových operačních systémech. Tento problém je vyřešen v budoucí aktualizaci produktu.

Některé hodnoty registru jsou nastaveny automaticky při prvním použití, pokud již nejsou nastaveny. Tento postup zajišťuje, že následné instalace používají stejné hodnoty. Tyto hodnoty jsou uloženy v `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`druhém klíči registru .

Můžete nastavit následující hodnoty registru:

| **Název** | **Typ** | **Výchozí** | **Popis** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ` nebo `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Balíčky | Adresář, kde jsou uloženy manifesty balíčku a volitelně datové části. Další informace naleznete na stránce [Zakázat nebo přesunout mezipaměť balíčku.](disable-or-move-the-package-cache.md) |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | Udržujte datové části balíčků i po jejich instalaci. Hodnotu můžete kdykoli změnit. Zakázáním zásady odeberete všechny datové části balíčků uložených v mezipaměti pro instanci, kterou opravíte nebo upravíte. Další informace naleznete na stránce [Zakázat nebo přesunout mezipaměť balíčku.](disable-or-move-the-package-cache.md) |
| `SharedInstallationPath` | `REG_SZ` nebo `REG_EXPAND_SZ` | %ProgramFiles(x86)%\Microsoft Visual Studio\Shared | Adresář, kde jsou nainstalovány některé balíčky sdílené mezi verzemi instancí sady Visual Studio. Hodnotu můžete kdykoli změnit, ale ovlivní to pouze budoucí instalace. Všechny produkty, které jsou již nainstalovány do starého umístění, nesmí být přesunuty nebo nemusí fungovat správně. |
| `BackgroundDownloadDisabled` |`REG_DWORD` | 1 | Zabrání instalačnímu programu v automatickém stahování aktualizací pro všechny nainstalované produkty sady Visual Studio. Hodnotu můžete kdykoli změnit. |

> [!IMPORTANT]
> Pokud po `CachePath` všech instalacích změníte zásady registru, musíte přesunout existující mezipaměť balíčku do `SYSTEM` `Administrators` nového umístění `Everyone` a ujistěte se, že je zabezpečená tak, aby měla úplné řízení a která má přístup pro čtení.
> Pokud se nepodaří přesunout existující mezipaměť nebo ji zabezpečit, může dojít k problémům s budoucími instalacemi.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

- [Instalace sady Visual Studio](install-visual-studio.md)
- [Zakázání nebo přesunutí mezipaměti balíčku](disable-or-move-the-package-cache.md)
- [Instalace sady Visual Studio pomocí parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
