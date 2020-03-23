---
title: 'Postup: Určení umístění souborů symbolů z příkazového řádku | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8aa067bb-e8bf-4081-aff0-cfbcf65934a0
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 604863cbef5e42b31450ea09dffa56a1a00ae992
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77476890"
---
# <a name="how-to-specify-symbol-file-locations-from-the-command-line"></a>Postup: Určení umístění souboru symbolů z příkazového řádku
Chcete-li zobrazit informace o symbolech, jako jsou názvy funkcí a čísla řádků, vyžaduje nástroj příkazového řádku VSPerfReport přístup ke symbolu (.* pdb*) profilovaných součástí a systémových souborů systému Windows. Soubory symbolů jsou vytvořeny při kompilaci komponenty. Další informace naleznete [v tématu VSPerfReport](../profiling/vsperfreport.md). VSPerfReport automaticky prohledává soubory symbolů v následujících umístěních:

- Cesty zadané ve volbě **/SymbolPath** nebo v **proměnné prostředí _NT_SYMBOL_PATH.**

- Přesnou místní cestu, kde byla komponenta zkompilován.

- Adresář, který obsahuje data profilování (.* vsp* nebo . *vsps*) Soubor.

  Společnost Microsoft poskytuje rozhraní . *pdb* soubory pro mnoho svých produktů on-line na symbol serveru. Pokud je počítač, který používáte pro vytváření sestav, připojen k Internetu, vsPerfReport se připojí k serveru symbolů online, aby automaticky vyhledáinformace o symbolech a uložil soubory do místního úložiště.

  Umístění souborů symbolů a úložiště serveru symbolů společnosti Microsoft můžete určit následujícími způsoby:

- Nastavte **proměnnou prostředí _NT_SYMBOL_PATH.**

- Přidejte volbu **/SymbolPath** do příkazového řádku VSPerfReport.

  Můžete také použít obě tyto metody.

> [!NOTE]
> Pokud [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] je nainstalován v místním počítači, umístění souborů symbolů systému Windows již pravděpodobně bylo zadáno. Další informace naleznete v [tématu How to: Reference Windows symbol information](../profiling/how-to-reference-windows-symbol-information.md). Stále je nutné nakonfigurovat VSPerfReport používat umístění a server, jak je popsáno dále v tomto tématu.

## <a name="specify-windows-symbol-files"></a>Určení souborů symbolů systému Windows

#### <a name="to-configure-the-use-of-the-windows-symbol-server"></a>Konfigurace použití symbolového serveru systému Windows

1. V případě potřeby vytvořte adresář pro místní uložení souborů symbolů.

2. Pomocí následující syntaxe nastavte proměnnou **_NT_SYMBOL_PATH** prostředí nebo volbu VSPerfReport /SymbolPath:

    `srv*<LocalStore>*https://msdl.microsoft.com/download/symbols`

    kde *<LocalStore>* je cesta k místnímu adresáři, který jste vytvořili.

## <a name="specify-component-symbol-files"></a>Určení souborů symbolů komponenty
 Profilování Nástroje hledá. *Pdb* soubory součástí, které chcete profilovat v původních umístěních, které jsou uloženy v součástech nebo ve složce, která obsahuje datový soubor profilování. Další umístění můžete zadat k prohledání přidáním jedné nebo více cest k **_NT_SYMBOL_PATH** nebo k volbě **/SymbolPath.** Samostatné cesty s středníky.

## <a name="example"></a>Příklad
 Následující příkazový řádek nastaví proměnnou **_NT_SYMBOL_PATH** prostředí na server se symboly systému Windows a místní adresář na **C:\Symbols**.

 ```cmd
  set  _NT_SYMBOL_PATH=srv*C:\symbols*https://msdl.microsoft.com/download/symbols
 ```

 Následující příkazový řádek VSPerfReport přidá adresář *C:\Projects\Symbols* do vyhledávací cesty pomocí možnosti **/SymbolPath.**

 **VSPerfReport**  *MyApp* **.exe /SymbolPath:C:\Projects\Symbols /summary:all**
