---
title: Výchozí nastavení v případě podnikového nasazení
description: Další informace o zásadách domény a dalších operací konfigurace pro podniková nasazení sady Visual Studio.
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 305b0398550a64722f6029a3d50082e6397643cb
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594523"
---
# <a name="set-defaults-for-enterprise-deployments-of-visual-studio"></a>Nastavení výchozích hodnot pro podniková nasazení sady Visual Studio

Můžete nastavit zásady registru, které ovlivňují nasazení sady Visual Studio. Tyto zásady jsou globální pro nový instalační program a ovlivnit:

- Kde jsou nainstalované některé balíčky sdílené s jinými verzemi nebo instance
- Kde jsou balíčky v mezipaměti
- Určuje, zda jsou všechny balíčky v mezipaměti

Můžete nastavit některé z těchto zásad, pomocí [možnosti příkazového řádku](use-command-line-parameters-to-install-visual-studio.md), nastavte hodnoty registru na počítači nebo dokonce distribuovat pomocí zásad skupiny v rámci celé organizace.

## <a name="registry-keys"></a>Klíče registru

Existuje několik umístění, kde můžete nastavit výchozí hodnoty enterprise a povolení jejich řízení pomocí zásad skupiny nebo přímo v registru. Visual Studio vyhledá postupně zobrazíte, pokud jsou nastavené žádné zásady organizace; co nejdříve po zjištění hodnota zásad v následujícím pořadí zbývající klíče jsou ignorovány.

1. `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup`
2. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`
3. `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\VisualStudio\Setup` (v 64bitových operačních systémech)

> [!IMPORTANT]
> Pokud nenastavíte `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup` klíče a místo toho nastavte jeden z jiných klíčů, měli byste nastavit oba klíče v 64bitových operačních systémech. Tento problém je vyřešen v budoucí aktualizace.

Některé hodnoty registru se nastaví automaticky při prvním, jsou použita, pokud nejsou již nastaven. Tento postup zajišťuje, že následné instalace použít stejné hodnoty. Tyto hodnoty jsou uloženy v klíči registru druhý `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`.

Můžete nastavit následující hodnoty registru:

| **Jméno** | **Typ** | **Default** | **Popis** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ` Nebo `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages | Ukládají se adresáře, kde manifesty balíček a volitelně datové části. Další informace najdete na stránce [Zakázání nebo přesunutí mezipaměti balíčku](disable-or-move-the-package-cache.md) . |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | Zachovejte datové části balíčku, i když jsou nainstalovány. Kdykoli můžete změnit hodnotu. Zakázání zásady odebere všechny datové části v mezipaměti balíčku pro instanci opravit nebo změnit. Další informace najdete na stránce [Zakázání nebo přesunutí mezipaměti balíčku](disable-or-move-the-package-cache.md) . |
| `SharedInstallationPath` | `REG_SZ` Nebo `REG_EXPAND_SZ` | %ProgramFiles(x86)%\Microsoft Visual Studio\Shared | Adresář, ve kterém jsou nainstalované některé balíčky sdíleny napříč verzemi instance sady Visual Studio. Hodnotu můžete kdykoli změnit, ale bude to mít vliv jenom na budoucí instalace. Jakékoli produkty, které jsou již nainstalovány do starého umístění, nesmí být přesunuty nebo nemusí fungovat správně. |
| `BackgroundDownloadDisabled` |`REG_DWORD` | 1 | Zabrání instalačnímu programu stahovat aktualizace automaticky pro všechny nainstalované produkty sady Visual Studio. Kdykoli můžete změnit hodnotu. |

> [!IMPORTANT]
> Změníte-li `CachePath` zásad registru po instalacích, je nutné přesunout existující mezipaměť balíčků do nového umístění a zajistit, aby byla zabezpečena, aby `SYSTEM` a `Administrators` měla úplnou kontrolu a `Everyone` mají přístup pro čtení.
> Nepovedlo se přesunout existující mezipaměť nebo ji zabezpečit, může to způsobit problémy s budoucími instalacemi.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také:

- [Instalace sady Visual Studio](install-visual-studio.md)
- [Zakázání nebo přesunutí mezipaměti balíčku](disable-or-move-the-package-cache.md)
- [Instalace sady Visual Studio s použitím parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
