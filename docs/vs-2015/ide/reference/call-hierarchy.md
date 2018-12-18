---
title: Hierarchie volání | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.CallHierarchy
helpviewer_keywords:
- Call Hierarchy
ms.assetid: c55bda01-d7de-4823-8f9a-1bcc37dbb74a
caps.latest.revision: 45
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 86cf4e12f412e6448f4a4b7c38af8268f10d9c56
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49851108"
---
# <a name="call-hierarchy"></a>Hierarchie volání
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Hierarchie volání umožňuje procházet váš kód zobrazením všechna volání do a z vybrané metody, vlastnosti nebo konstruktoru. To vám umožní lépe porozumět toku kódu a vyhodnotit vliv změn kódu. Můžete zkontrolovat několik úrovní kód zobrazení komplexní řetězů, volání metod a další vstupní body k kód, který umožňuje prozkoumat všemi možnými cestami spuštění.  
  
 Hierarchie volání je k dispozici v době návrhu, na rozdíl od zásobníku volání, který je zobrazené ladicím programem.  
  
## <a name="using-call-hierarchy"></a>Pomocí hierarchie volání  
 Chcete-li zobrazit **hierarchie volání** okna, klikněte pravým tlačítkem na název metody, vlastnosti nebo volání konstruktoru a potom klikněte na tlačítko **zobrazit hierarchii volání**.  
  
 Název člena se zobrazí v podokně se stromovým zobrazením v **hierarchie volání** okna. Pokud rozbalíte uzel člen **volání do**_název člena_ a **volání z**_název člena_ zobrazí podřízených uzlů. Následující obrázek znázorňuje tyto uzly v **hierarchie volání** okna.  
  
 ![Hierarchie volání s jedním uzlem otevřené](../../ide/reference/media/onenode.png "OneNode")  
Hierarchie volání – okno  
  
- Pokud rozbalíte **volání do** uzlu, všechny členy, že se zobrazují volání vybraného členu.  
  
- Pokud rozbalíte **volání z** se zobrazí uzel, všechny členy, které jsou volány vybraného členu.  
  
  Každý z těchto členů poduzlu do potom rozbalte **volání do** a **volání z** uzly. Díky tomu můžete přejít do zásobníku volání, jak je znázorněno na následujícím obrázku.  
  
  ![Otevřít více uzlů hierarchie volání](../../ide/media/multiplenodes.png "MultipleNodes")  
  Hierarchie volání – okno  
  
  Pro členy, které jsou definovány jako virtuální nebo abstraktní **název metody přepsání** uzel se objeví. Pro členy rozhraní **název metody implementuje** uzel se objeví. Tyto uzly rozšíření se zobrazí na stejné úrovni jako **volání do** a **volání z** uzly.  
  
  **Obor vyhledávání** na panelu nástrojů obsahuje možnosti pro **Moje řešení**, **aktuální projekt**, a **aktuální dokument**.  
  
  Když vyberete podřízeného člena v **hierarchie volání** podokně se stromovým zobrazením:  
  
- **Hierarchie volání** podokně podrobností se zobrazí všechny řádky kódu, ve kterém tento podřízený člen je volána z nadřazeného člena.  
  
- **Okno Definice kódu**, pokud otevřete, zobrazí kód pro vybraného členu. Toto okno je k dispozici v jazyce C# a C++. Další informace o tomto okně najdete v tématu [zobrazení struktury kódu](../../ide/viewing-the-structure-of-code.md).  
  
> [!NOTE]
>  Hierarchie volání nenajde metoda odkazy na skupinu obsahující místa, kde se přidá jako obslužná rutina události metodu, nebo je přiřazená delegáta. Pokud chcete najít všechny odkazy na metodu, můžete použít **najít všechny odkazy** příkazu.  
  
## <a name="shortcut-menu-items"></a>Položky místní nabídky  
 Následující tabulka popisuje několik možnosti místní nabídky, které jsou k dispozici, když kliknete pravým tlačítkem myši na uzel v podokně se stromovým zobrazením.  
  
|Položka kontextové nabídky|Popis|  
|-----------------------|-----------------|  
|**Přidat jako nový kořen**|Přidá zvolený uzel podokně se stromovým zobrazením jako nový kořenový uzel. To umožňuje zaměřit se na konkrétní podstrom vaši pozornost.|  
|**Odebrat kořen**|Odebere vybrané kořenový uzel v podokně se stromovým zobrazením. Tato možnost je dostupná pouze z kořenového uzlu.<br /><br /> Můžete také použít **odebrat kořenové** tlačítka panelu nástrojů, které chcete odebrat vybrané kořenového uzlu.|  
|**Přejít k definici**|Spustí příkaz Přejít k definici ve zvoleném uzlu. Toto odkazuje na původní definice pro člen volání nebo definicí proměnné.<br /><br /> Ke spuštění příkazu Přejít k definici, můžete také dvakrát klikněte na vybraný uzel nebo stisknutím klávesy F12 ve zvoleném uzlu.|  
|**Najít všechny odkazy**|Spustí příkaz Najít všechny odkazy na vybraný uzel. To tuto referenční třídu nebo člen vyhledá všechny řádky kódu ve vašem projektu.<br /><br /> SHIFT + F12 můžete také použít ke spuštění příkazu Najít všechny odkazy na vybraný uzel.|  
|**kopírování**|Zkopíruje obsah vybraného uzlu (ale ne jeho podřízené uzly).|  
|**Aktualizace**|Sbalí vybraný uzel tak, aby znovu ho rozbalíte, zobrazí aktuální informace.|



