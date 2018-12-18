---
title: 'Postupy: určení umístění souboru se symboly z příkazového řádku | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 8aa067bb-e8bf-4081-aff0-cfbcf65934a0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 498720ff5b76ce2c3229c9c7a493023318213ae4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49941929"
---
# <a name="how-to-specify-symbol-file-locations-from-the-command-line"></a>Postupy: určení umístění souboru se symboly z příkazového řádku
Chcete-li zobrazit informace o symbolech, jako jsou názvy funkcí a čísla řádků, příkazového řádku nástroje VSPerfReport vyžaduje přístup k symbolu (. *soubor PDB*) soubory profilovaných komponent a souborů systému Windows. Soubory symbolů se vytvoří při kompilaci komponentu. Další informace najdete v tématu [VSPerfReport](../profiling/vsperfreport.md). VSPerfReport automaticky vyhledá soubory symbolů v následujících umístěních:  
  
- Cesty zadané **/symbolpath** možnost nebo v **_NT_SYMBOL_PATH** proměnné prostředí.  
  
- Přesné místní cesta kde byl zkompilován komponentu.  
  
- Adresář, který obsahuje data profilace (. *Vsp* nebo. *vsps*) soubor.  
  
  Společnost Microsoft poskytuje. *pdb* soubory pro celou řadu jejích produktů online na serveru symbolů. Pokud počítač, který používáte pro vytváření sestav je připojený k Internetu, VSPerfReport připojí k serveru symbolů online automaticky vyhledat informace o symbolech a uložte soubory do místního úložiště.  
  
  Zadejte umístění souborů symbolů a úložišti Microsoft symbol server následujícími způsoby:  
  
- Nastavte **_NT_SYMBOL_PATH** proměnné prostředí.  
  
- Přidat **/symbolpath** možnost příkazového řádku VSPerfReport.  
  
  Můžete také použít obě tyto metody.  
  
> [!NOTE]
>  Pokud [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] je nainstalována na místním počítači, do umístění pro soubory symbolů Windows pravděpodobně nebyl zadán již. Další informace najdete v tématu [jak: informace o symbolech Windows odkaz](../profiling/how-to-reference-windows-symbol-information.md). Stále je nutné nakonfigurovat nastavení nástroje VSPerfReport pro umístění a serveru, jak je popsáno dále v tomto tématu.  
  
## <a name="specify-windows-symbol-files"></a>Zadejte soubory symbolů Windows  
  
#### <a name="to-configure-the-use-of-the-windows-symbol-server"></a>Můžete konfigurovat použití Windows serveru symbolů  
  
1. V případě potřeby vytvořte adresář pro uložení souborů symbolů místně.  
  
2. Použijte následující syntax k nastavení **_NT_SYMBOL_PATH** proměnné prostředí nebo možnost VSPerfReport/symbolpath:  
  
    **SRV\\*** *LocalStore* **\*http://msdl.microsoft.com/downloads/symbols**  
  
    kde *LocalStore* je cesta k místnímu adresáři, který jste vytvořili.  
  
## <a name="specify-component-symbol-files"></a>Zadejte soubory symbolů komponenty  
 Vyhledá nástroje pro profilaci. *pdb* souborů komponent, které chcete do profilu do jejich původního umístění, které jsou uloženy v součásti nebo ve složce, která obsahuje soubor dat profilování. Můžete zadat jiné umístění pro hledání tak, že přidáte jednu nebo více cest k **_NT_SYMBOL_PATH** nebo **/symbolpath** možnost. Samostatné cesty oddělte středníkem.  
  
## <a name="example"></a>Příklad  
 Následující příkazový řádek sady **_NT_SYMBOL_PATH** proměnnou prostředí pro Windows server symbolů a místní adresář, do **C:\Symbols**.  
  
 **Nastavte _NT_SYMBOL_PATH = srv\*C:\symbols\*http://msdl.microsoft.com/downloads/symbols**  
  
 Následující příkaz VSPerfReport přidá *C:\Projects\Symbols* adresář do cesty pro hledání pomocí **/symbolpath** možnost.  
  
 **VSPerfReport***MyApp* **Summary /SymbolPath:C:\Projects\Symbols .exe**