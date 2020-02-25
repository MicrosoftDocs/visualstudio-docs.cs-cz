---
title: 'Postupy: určení umístění souborů symbolů z příkazového řádku | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 8aa067bb-e8bf-4081-aff0-cfbcf65934a0
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 01fbb6cfd1717562af79c067ede0cad9753ad5dd
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557901"
---
# <a name="how-to-specify-symbol-file-locations-from-the-command-line"></a>Postupy: Určení umístění souboru se symboly z příkazového řádku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chcete-li zobrazit informace o symbolech, jako jsou názvy funkcí a čísla řádků, nástroj příkazového řádku VSPerfReport vyžaduje přístup k souborům symbolů (. pdb) souborů profilované komponenty a systémových souborů systému Windows. Soubory symbolů se vytvoří, když je komponenta zkompilována. Další informace najdete v tématu [VSPerfReport](../profiling/vsperfreport.md). VSPerfReport automaticky hledá v těchto umístěních soubory symbolů:  
  
- Cesty zadané v možnosti **/SymbolPath** nebo v proměnné prostředí **_NT_SYMBOL_PATH** .  
  
- Přesná místní cesta, kde byla komponenta zkompilována.  
  
- Adresář, který obsahuje soubor dat profilování (. vsp nebo. vsps).  
  
  Microsoft poskytuje soubory. PDB pro spoustu svých produktů online na serveru symbolů. Pokud je počítač, který používáte pro vytváření sestav, připojený k Internetu, VSPerfReport se připojí k serveru symbolů online a automaticky vyhledá informace o symbolech a uloží soubory do místního úložiště.  
  
  Můžete zadat umístění souborů symbolů a úložiště Microsoft symbol server, a to následujícími způsoby:  
  
- Nastavte proměnnou prostředí **_NT_SYMBOL_PATH** .  
  
- Přidejte možnost **/SymbolPath** do příkazového řádku VSPerfReport.  
  
  Obě tyto metody můžete použít také.  
  
> [!NOTE]
> Pokud je v místním počítači nainstalováno [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], umístění souborů symbolů systému Windows pravděpodobně bylo již zadáno. Další informace naleznete v tématu [How to: Reference Windows symbol Information](../profiling/how-to-reference-windows-symbol-information.md). Pořád musíte nakonfigurovat VSPerfReport, aby používal umístění a server, jak je popsáno dále v tomto tématu.  
  
## <a name="specifying-windows-symbol-files"></a>Určení souborů symbolů systému Windows  
  
#### <a name="to-configure-the-use-of-the-windows-symbol-server"></a>Postup při konfiguraci použití serveru symbolů systému Windows  
  
1. V případě potřeby vytvořte adresář pro místní ukládání souborů symbolů.  
  
2. Pomocí následující syntaxe nastavte proměnnou prostředí **_NT_SYMBOL_PATH** nebo možnost VSPerfReport/SymbolPath:  
  
   `srv*<LocalStore>*https://msdl.microsoft.com/downloads/symbols`  
  
   kde *<LocalStore>* je cesta k místnímu adresáři, který jste vytvořili.  
  
## <a name="specifying-component-symbol-files"></a>Určení souborů symbolů součásti  
 Nástroje pro profilaci vyhledá soubory. pdb komponent, které chcete profilovat, v původních umístěních uložených v součástech nebo ve složce, která obsahuje soubor dat profilování. Přidáním jedné nebo více cest k **_NT_SYMBOL_PATH** nebo k možnosti **/SymbolPath** můžete určit další umístění pro hledání. Jednotlivé cesty oddělte středníkem.  
  
## <a name="example"></a>Příklad  
 Následující příkazový řádek nastaví proměnnou prostředí **_NT_SYMBOL_PATH** na server symbolů systému Windows a místní adresář na **C:\Symbols**.  

 ```cmd
 set  _NT_SYMBOL_PATH=srv*C:\symbols*https://msdl.microsoft.com/downloads/symbols
 ```

 Následující příkazový řádek VSPerfReport přidá adresář C:\Projects\Symbols do cesty pro hledání pomocí možnosti **/SymbolPath** .  
  
 **VSPerfReport**  *MyApp* **. exe/SymbolPath: C:\Projects\Symbols/Summary: vše**
