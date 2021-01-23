---
title: Určení umístění souborů symbolů z příkazového řádku
description: Přečtěte si, jak nástroj příkazového řádku VSPerfReport vyžaduje přístup k souborům symbolů (. pdb), aby zobrazoval informace o symbolech, jako jsou názvy funkcí a čísla řádků.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 8aa067bb-e8bf-4081-aff0-cfbcf65934a0
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7a9a801ccf7493675e49a3cde6ef91675e5f1189
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721915"
---
# <a name="how-to-specify-symbol-file-locations-from-the-command-line"></a>Postupy: určení umístění souborů symbolů z příkazového řádku
Chcete-li zobrazit informace o symbolech, jako jsou názvy funkcí a čísla řádků, nástroj příkazového řádku VSPerfReport vyžaduje přístup k symbolu (.*PDB*) soubory profilované komponenty a systémové soubory systému Windows. Soubory symbolů se vytvoří, když je komponenta zkompilována. Další informace najdete v tématu [VSPerfReport](../profiling/vsperfreport.md). VSPerfReport automaticky hledá v těchto umístěních soubory symbolů:

- Cesty zadané v možnosti **/SymbolPath** nebo v proměnné prostředí **_NT_SYMBOL_PATH** .

- Přesná místní cesta, kde byla komponenta zkompilována.

- Adresář, který obsahuje data profilace (.*VSP* nebo. *vsps*) souborů.

  Společnost Microsoft poskytuje. soubory *PDB* pro mnoho svých produktů online na serveru symbolů. Pokud je počítač, který používáte pro vytváření sestav, připojený k Internetu, VSPerfReport se připojí k serveru symbolů online a automaticky vyhledá informace o symbolech a uloží soubory do místního úložiště.

  Můžete zadat umístění souborů symbolů a úložiště Microsoft symbol server, a to následujícími způsoby:

- Nastavte proměnnou prostředí **_NT_SYMBOL_PATH** .

- Přidejte možnost **/SymbolPath** do příkazového řádku VSPerfReport.

  Obě tyto metody můžete použít také.

> [!NOTE]
> Pokud [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] je v místním počítači nainstalováno, umístění souborů symbolů systému Windows je pravděpodobně již zadáno. Další informace naleznete v tématu [How to: Reference Windows symbol Information](../profiling/how-to-reference-windows-symbol-information.md). Pořád musíte nakonfigurovat VSPerfReport, aby používal umístění a server, jak je popsáno dále v tomto tématu.

## <a name="specify-windows-symbol-files"></a>Zadat soubory symbolů Windows

#### <a name="to-configure-the-use-of-the-windows-symbol-server"></a>Postup při konfiguraci použití serveru symbolů systému Windows

1. V případě potřeby vytvořte adresář pro místní ukládání souborů symbolů.

2. Pomocí následující syntaxe nastavte proměnnou prostředí **_NT_SYMBOL_PATH** nebo možnost VSPerfReport/SymbolPath:

    `srv*<LocalStore>*https://msdl.microsoft.com/download/symbols`

    kde *<LocalStore>* je cesta k místnímu adresáři, který jste vytvořili.

## <a name="specify-component-symbol-files"></a>Zadat soubory symbolů součásti
 Nástroje pro profilaci vyhledá. soubory *PDB* komponent, které chcete profilovat v původních umístěních uložených v součástech, nebo ve složce, která obsahuje soubor dat profilování. Přidáním jedné nebo více cest k **_NT_SYMBOL_PATH** nebo k možnosti **/SymbolPath** můžete určit další umístění pro hledání. Jednotlivé cesty oddělte středníkem.

## <a name="example"></a>Příklad
 Následující příkazový řádek nastaví proměnnou prostředí **_NT_SYMBOL_PATH** na server symbolů systému Windows a místní adresář na **C:\Symbols**.

 ```cmd
  set  _NT_SYMBOL_PATH=srv*C:\symbols*https://msdl.microsoft.com/download/symbols
 ```

 Následující příkazový řádek VSPerfReport přidá adresář *C:\Projects\Symbols* do cesty pro hledání pomocí možnosti **/SymbolPath** .

 **VSPerfReport**  *MyApp* **. exe/SymbolPath: C:\Projects\Symbols/Summary: vše**
