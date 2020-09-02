---
title: Konfigurace zobrazení oken nástrojů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, configuring
- tool windows, appearance
ms.assetid: 502a4926-bb83-473e-94e2-8e833c5f8b53
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1af78bd58c42cf1312e36621011802e908c9e919
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186399"
---
# <a name="tool-window-display-configuration"></a>Konfigurace zobrazení oken nástrojů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Když VSPackage zaregistruje okno nástroje, výchozí pozice, velikost, ukotvení stylu a další informace o viditelnosti se zadává v volitelných hodnotách. Další informace o registraci okna nástrojů naleznete v tématu [okna nástrojů v registru](../extensibility/tool-windows-in-the-registry.md) .  
  
## <a name="window-display-information"></a>Informace o zobrazení okna  
 Základní konfigurace zobrazení v okně nástroje je uložena až do šesti volitelných hodnot:  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              (Default)       = reg_sz: <Package GUID>Name            = reg_sz: <name of tool window>Float           = reg_sz: <position>Style           = reg_sz: <dock style>Window          = reg_sz: <window GUID>Orientation     = reg_sz: <orientation>DontForceCreate = reg_dword: 0x00000000  
```  
  
|Název|Typ|Data|Popis|  
|----------|----------|----------|-----------------|  
|Název|REG_SZ|"Stručný název bude doplněn"|Krátký název, který popisuje okno nástroje. Používá se pouze pro referenci v registru.|  
|Float|REG_SZ|X1, Y1, X2, Y2|Čtyři čárkami oddělené hodnoty. X1, Y1 je souřadnice levého horního rohu okna nástroje. X2, Y2 je souřadnice pravého dolního rohu. Všechny hodnoty jsou v souřadnicích obrazovky.|  
|Styl|REG_SZ|MDI<br /><br /> Plovák<br /><br /> Spojeného<br /><br /> S kartami<br /><br /> "AlwaysFloat"|Klíčové slovo určující počáteční stav zobrazení okna nástroje.<br /><br /> "MDI" = docked s oknem MDI.<br /><br /> "Float" = float.<br /><br /> "Propojený" = propojený s jiným oknem (zadané v položce okna).<br /><br /> "S kartami" v kombinaci s jiným oknem nástrojů.<br /><br /> "AlwaysFloat" = nelze ukotvit.<br /><br /> Další informace najdete v části komentáře níže.|  
|Okno|REG_SZ|*\<GUID>*|Identifikátor GUID okna, na které může být panel nástrojů propojen nebo s kartami. Identifikátor GUID může patřit do jedné z vašich vlastních oken nebo jednoho z oken v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrovaném vývojovém prostředí.|  
|Orientace|REG_SZ|Zbývá<br /><br /> Kliknutím<br /><br /> Vrchol<br /><br /> Dolů|Viz část komentáře.|  
|DontForceCreate|REG_DWORD|0 nebo 1|Pokud je tato položka přítomná a její hodnota není nula, okno se načte, ale nezobrazí se hned.|  
  
### <a name="comments"></a>Komentáře  
 Položka orientace definuje pozici, kde je ukotveno okno nástroje, když je dvakrát kliknuto na jeho záhlaví. Pozice je relativní vzhledem k oknu určenému v položce okna. Pokud je položka Style nastavena na hodnotu "propojený", položka orientace může být "Left", "Right", "Top" nebo "Bottom". Pokud je položka stylu "s kartami", položka orientace může být "Left" nebo "Right" a určuje, kam je karta přidána. Pokud je položka stylu "float", okno nástroje je nejprve plovoucí. Po dvojitém kliknutí na záhlaví a použití položek v okně se použije styl "s kartami". Pokud je položka stylu "AlwaysFloat", okno nástroje nelze ukotvit. Pokud je položka stylu "MDI", okno nástroje je propojeno s oblastí MDI a položka okna je ignorována.  
  
### <a name="example"></a>Příklad  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {A0C5197D-0AC7-4B63-97CD-8872A789D233}\  
              (Default)       = reg_sz: {DA9FB551-C724-11D0-AE1F-00A0C90FFFC3}  
              DontForceCreate = reg_dword: 0x00000000  
              Float           = reg_sz: 100,100,450,300  
              Name            = reg_sz: Bookmarks  
              Orientation     = reg_sz: Left  
              Style           = reg_sz: Tabbed  
              Window          = reg_sz: {34E76E81-EE4A-11D0-00A0C90FFFC3}  
```  
  
## <a name="tool-window-visibility"></a>Viditelnost okna nástrojů  
 Hodnoty v volitelném podklíči viditelnosti určují nastavení viditelnosti okna nástroje. Názvy hodnot se používají k ukládání identifikátorů GUID příkazů, které vyžadují viditelnost okna. Je-li příkaz spuštěn, rozhraní IDE garantuje, že okno nástroje je vytvořeno a zobrazeno.  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              Visibility\  
                (Default) = reg_sz:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_sz:  
```  
  
|Název|Typ|Data|Popis|  
|----------|----------|----------|-----------------|  
|(Výchozí)|REG_SZ|Žádné|Nechejte prázdné.|  
|*\<GUID>*|REG_DWORD nebo REG_SZ|0 nebo popisný řetězec.|Nepovinný parametr. Název položky musí být identifikátor GUID příkazu, který vyžaduje viditelnost. Hodnota pouze obsahuje informativní řetězec. Obvykle je hodnota `reg_dword` nastavena na 0.|  
  
### <a name="example"></a>Příklad  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {EEFA5220-E298-11D0-8F78-00A0C9110057}\  
              Visibility\  
                (Default) = reg_sz:  
                {93694fa0-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
                {9DA22B82-6211-11d2-9561-00600818403B} = reg_dword: 0x00000000  
                {adfc4e66-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
```  
  
## <a name="see-also"></a>Viz také  
 [Základy VSPackage](../misc/vspackage-essentials.md)
