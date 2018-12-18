---
title: Zakázání nebo přesunutí mezipaměti balíčku
description: Zjistěte, jak zakázat, povolit nebo přesunutí mezipaměti balíčku pro nasazení sady Visual Studio.
ms.date: 04/14/2017
ms.technology: vs-acquisition
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- cache
- nocache
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 2429993A-3F0E-41C5-9562-FEA6AE994440
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 006e7112a2b6c7b990fb412c6a9a2c458bc9e8b2
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159539"
---
# <a name="disable-or-move-the-package-cache"></a>Zakázání nebo přesunutí mezipaměti balíčku

Mezipaměť balíčků poskytuje zdroj balíčků nainstalovaných v případě, že potřebujete opravit Visual Studio nebo další související produkty v případech, kdy mají bez připojení k Internetu. Některé disky nebo systém nastavit ups, ale možná chcete zachovat tyto balíčky kolem.
Instalační program stáhne je podle potřeby, takže pokud chcete uložit nebo obnovení místo na disku můžete zakázat nebo přesunutí mezipaměti balíčku.

## <a name="disable-the-package-cache"></a>Zakázat mezipaměť balíčku

Před instalací, upravit nebo opravte Visual Studio nebo jiné produkty s novým instalačním programem, můžete spustit instalační program s `--nocache` přepnout do instalačního programu.

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" --nocache
```

Všechny operace, které vám v žádném produktu odebere všechny existující balíčky pro tento produkt a vyhnete se ukládají všechny balíčky, které se po instalaci. Pokud upravíte nebo opravte Visual Studio a balíčky jsou požadovány, bude se automaticky se stáhne a odebrána po instalaci.

Pokud chcete znovu povolit mezipaměť, předejte `--cache` místo. Pouze balíčky, které jsou požadovány se uloží do mezipaměti, takže pokud potřebujete obnovit všechny balíčky, měli byste opravit Visual Studio před odpojením z vaší sítě.

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" repair --passive --norestart --cache
```

Můžete také nastavit `KeepDownloadedPayloads` [zásad registru](set-defaults-for-enterprise-deployments.md) zakázání ukládání do mezipaměti, před instalací, upravit nebo opravte Visual Studio.

## <a name="move-the-package-cache"></a>Přesunutí mezipaměti balíčku

Běžnou konfigurací systému je mít pro vývoj pro Windows nainstalované na SSD s větší pevného disku (nebo více) potřebuje, jako je zdrojový kód, binární soubory aplikace a další. Pokud chcete pracovat v režimu offline můžete místo toho přesunutí mezipaměti balíčku.

V současné době můžete provést jen pokud jste nastavili `CachePath` [zásad registru](set-defaults-for-enterprise-deployments.md) před instalací, upravit nebo opravte Visual Studio.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také:

* [Instalace sady Visual Studio](install-visual-studio.md)
* [Výchozí nastavení v případě podnikového nasazení](set-defaults-for-enterprise-deployments.md)
* [Instalace sady Visual Studio s použitím parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
