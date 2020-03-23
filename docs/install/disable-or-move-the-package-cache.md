---
title: Zakázání nebo přesunutí mezipaměti balíčku
description: Zjistěte, jak zakázat, povolit nebo přesunout mezipaměť balíčků pro nasazení sady Visual Studio.
ms.date: 04/14/2017
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- cache
- nocache
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 2429993A-3F0E-41C5-9562-FEA6AE994440
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 3f38757931cb22e9072571d96b015f37882dd500
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114788"
---
# <a name="disable-or-move-the-package-cache"></a>Zakázání nebo přesunutí mezipaměti balíčku

Mezipaměť balíčku poskytuje zdroj nainstalovaných balíčků v případě, že potřebujete opravit sady Visual Studio nebo jiné související produkty v případech, kdy nemáte připojení k Internetu. U některých jednotek nebo nastavení systému však možná nebudete chtít ponechat všechny tyto balíčky v okolí.
Instalační program je v případě potřeby stáhne, takže pokud chcete uložit nebo obnovit místo na disku, můžete zakázat nebo přesunout mezipaměť balíčku.

## <a name="disable-the-package-cache"></a>Zakázání mezipaměti balíčku

Před instalací, úpravou nebo opravou sady Visual Studio nebo jiných produktů pomocí `--nocache` nového instalačního programu můžete spustit instalační program s přepínačem na instalační program.

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" --nocache
```

Všechny operace, které provedete s jakýmkoli produktem, odeberou všechny existující balíčky pro tento produkt a vyhnou se uložení balíčků po jejich instalaci. Pokud upravíte nebo opravíte sady Visual Studio a balíčky budou automaticky staženy a odebrány po jejich instalaci.

Pokud chcete znovu povolit mezipaměť, předaj `--cache` místo toho. Pouze balíčky, které jsou požadovány budou uloženy do mezipaměti, takže pokud potřebujete obnovit všechny balíčky, měli byste opravit Visual Studio před odpojením od sítě.

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" repair --passive --norestart --cache
```

Můžete také nastavit `KeepDownloadedPayloads` [zásady registru](set-defaults-for-enterprise-deployments.md) zakázat mezipaměť před instalací, úpravou nebo opravou sady Visual Studio.

## <a name="move-the-package-cache"></a>Přesunutí mezipaměti balíčku

Běžnou konfigurací systému je mít systém Windows nainstalovaný na ssd disku s větším pevným diskem (nebo více) pro potřeby vývoje, jako je zdrojový kód, binární soubory programů a další. Pokud chcete pracovat offline, můžete místo toho přesunout mezipaměť balíčku.

V současné době to lze provést `CachePath` pouze v případě, že před instalací, úpravou nebo opravou sady Visual Studio nastavíte [zásady registru.](set-defaults-for-enterprise-deployments.md)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Instalace sady Visual Studio](install-visual-studio.md)
* [Nastavení výchozích hodnot pro podniková nasazení](set-defaults-for-enterprise-deployments.md)
* [Instalace sady Visual Studio pomocí parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
