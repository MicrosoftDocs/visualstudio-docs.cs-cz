---
title: 'Postupy: určení umístění souboru se symboly z příkazového řádku | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8aa067bb-e8bf-4081-aff0-cfbcf65934a0
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3d138166bc0dfdf93df5d4e340fc0d0a62d1828b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51721187"
---
# <a name="how-to-specify-symbol-file-locations-from-the-command-line"></a>Postupy: Určení umístění souboru se symboly z příkazového řádku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vsperfreport – nástroj příkazového řádku k zobrazení informací o symbolu, jako jsou názvy funkcí a čísla řádků, vyžaduje přístup k soubory symbolů (PDB) PROFILOVANÉHO komponent a souborů systému Windows. Soubory symbolů se vytvoří při kompilaci komponentu. Další informace najdete v tématu [VSPerfReport](../profiling/vsperfreport.md). VSPerfReport automaticky vyhledá soubory symbolů v následujících umístěních:  
  
- Cesty zadané **/symbolpath** možnost nebo v **_NT_SYMBOL_PATH** proměnné prostředí.  
  
- Přesné místní cesta kde byl zkompilován komponentu.  
  
- Adresář obsahující soubor dat profilování (.vsp nebo .vsps).  
  
  Společnost Microsoft poskytuje soubory s příponou .pdb pro spoustu jejích produktů online na serveru symbolů. Pokud počítač, který používáte pro vytváření sestav je připojený k Internetu, VSPerfReport připojí k serveru symbolů online automaticky vyhledat informace o symbolech a uložte soubory do místního úložiště.  
  
  Zadejte umístění souborů symbolů a úložišti Microsoft symbol server následujícími způsoby:  
  
- Nastavte **_NT_SYMBOL_PATH** proměnné prostředí.  
  
- Přidat **/symbolpath** možnost příkazového řádku VSPerfReport.  
  
  Můžete také použít obě tyto metody.  
  
> [!NOTE]
>  Pokud [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] je nainstalována na místním počítači, do umístění pro soubory symbolů Windows pravděpodobně nebyl zadán již. Další informace najdete v tématu [postupy: odkaz na informace o symbolech Windows](../profiling/how-to-reference-windows-symbol-information.md). Stále musíte nakonfigurovat nastavení nástroje VSPerfReport pro umístění a serveru, jak je popsáno dále v tomto tématu.  
  
## <a name="specifying-windows-symbol-files"></a>Zadat soubory symbolů Windows  
  
#### <a name="to-configure-the-use-of-the-windows-symbol-server"></a>Můžete konfigurovat použití Windows serveru symbolů  
  
1. V případě potřeby vytvořte adresář pro uložení souborů symbolů místně.  
  
2. Použijte následující syntax k nastavení **_NT_SYMBOL_PATH** proměnné prostředí nebo možnost VSPerfReport/symbolpath:  
  
    **SRV\\*** *LocalStore* **\*http://msdl.microsoft.com/downloads/symbols**  
  
    kde *LocalStore* je cesta k místnímu adresáři, který jste vytvořili.  
  
## <a name="specifying-component-symbol-files"></a>Určení souborů symbolů komponenty  
 Profilování nástroje hledá soubory the.pdb komponent, které chcete do profilu do jejich původního umístění, které jsou uloženy v součásti nebo ve složce, která obsahuje soubor dat profilování. Můžete zadat jiné umístění pro hledání tak, že přidáte jednu nebo více cest k **_NT_SYMBOL_PATH** nebo **/symbolpath** možnost. Samostatné cesty oddělte středníkem.  
  
## <a name="example"></a>Příklad  
 Následující příkazový řádek sady **_NT_SYMBOL_PATH** proměnnou prostředí pro Windows server symbolů a místní adresář, do **C:\Symbols**.  
  
 **Nastavte _NT_SYMBOL_PATH = srv\*C:\symbols\*http://msdl.microsoft.com/downloads/symbols**  
  
 Následující příkaz VSPerfReport přidá C:\Projects\Symbols adresář do cesty pro hledání pomocí **/symbolpath** možnost.  
  
 **VSPerfReport***MyApp* **Summary /SymbolPath:C:\Projects\Symbols .exe**



