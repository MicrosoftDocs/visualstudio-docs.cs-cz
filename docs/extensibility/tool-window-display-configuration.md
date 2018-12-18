---
title: Nástroj pro konfiguraci zobrazení okna | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, configuring
- tool windows, appearance
ms.assetid: 502a4926-bb83-473e-94e2-8e833c5f8b53
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 087fc8bc20b8ed70001b44ae06c614fad58c1439
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49839697"
---
# <a name="tool-window-display-configuration"></a>Konfigurace zobrazení okna nástroje
Pokud VSPackage zaregistruje panelu nástrojů, výchozí umístění, velikost, styl ukotvení a další informace o viditelnosti se zadává v volitelné hodnoty. Další informace o registraci okna nástroje, najdete v části [nástroj Windows v registru](../extensibility/tool-windows-in-the-registry.md)  

## <a name="window-display-information"></a>Informace o zobrazení okna  
 Panel nástrojů zobrazení základní konfigurace je uložená v až šest volitelné hodnoty:  

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


| Název | Typ | Data | Popis |
|-----------------|-----------| - | - |
| Název | REG_SZ | "Krátký název místo" | Krátký název, který popisuje panel nástrojů. Použít pouze pro referenci v registru. |
| plovoucí desetinnou čárkou | REG_SZ | "X1, Y1, X2, Y2" | Čtyři hodnoty oddělené čárkami. X1, Y1 je souřadnice levého horního rohu panelu nástrojů. X2, Y2 je souřadnice pravého dolního rohu. Všechny hodnoty jsou souřadnice obrazovky. |
| Styl | REG_SZ | "MDI"<br /><br /> "Float"<br /><br /> "Propojené"<br /><br /> "S kartami"<br /><br /> "AlwaysFloat" | Klíčové slovo určující počáteční zobrazit stav panelu nástrojů.<br /><br /> "MDI" = ukotven pomocí okna MDI.<br /><br /> "Float" = s plovoucí desetinnou čárkou.<br /><br /> "Propojené" = propojené se jiné okno (zadané v položce okno).<br /><br /> "S kartami" = v kombinaci s další okno nástroje.<br /><br /> "AlwaysFloat" = nelze ukotvit.<br /><br /> Další informace najdete v oddílu pro komentáře. |
| Okno | REG_SZ | *\<IDENTIFIKÁTOR GUID &GT;* | Identifikátor GUID okna, ke kterému můžete propojené okno nástroje nebo s kartami. Identifikátor GUID může patřit do jedné vlastní windows nebo některý z windows v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrovaného vývojového prostředí. |
| Orientace | REG_SZ | "Left"<br /><br /> "Právo"<br /><br /> "Top"<br /><br /> "Dolů" | Najdete v oddílu pro komentáře. |
| DontForceCreate | REG_DWORD | 0 nebo 1 | Pokud je tato položka a její hodnota není nula, v okně je načten, ale nikoliv okamžitě zobrazí. |

### <a name="comments"></a>Komentáře  
 Orientace položka udává pozici, kde se panel nástrojů ukotvené při poklepání na záhlaví. Pozice je vzhledem k oknu zadané v položce okna. Pokud styl položka má nastavenou hodnotu "Propojené", orientace položka může být "Vlevo", "Vpravo", "Top" nebo "Dolů". Pokud položka Style je "Tabbed", orientace položka může být "vlevo" nebo "Vpravo" a určuje, kde se přidá na kartu. Pokud je položka styl "Float", panel nástrojů čísel s plovoucí čárkou nejprve. Při poklepání na záhlaví okna použít položky orientaci a okna a okna používá "Tabbed" style. Pokud je položka styl "AlwaysFloat", nelze ukotvit okno nástroje. Pokud je položka styl "MDI", panel nástrojů je propojený s oblasti MDI a okno Položka je ignorována.  

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

## <a name="tool-window-visibility"></a>Viditelnost okna nástroje  
 Hodnoty v podklíči volitelné viditelnost určují nastavení viditelnost panelu nástrojů. Názvy hodnoty se používají k ukládání GUID příkazy, které vyžadují viditelnost okna. Pokud je proveden příkaz, rozhraní IDE zaručuje, že panel nástrojů je vytvořena a nastavena jako viditelná.  

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
|(Výchozí)|REG_SZ|Žádné|Nechte prázdné.|  
|*\<IDENTIFIKÁTOR GUID &GT;*|REG_DWORD nebo REG_SZ|0 nebo popisný řetězec.|Volitelné. Název položky musí být identifikátor GUID příkaz vyžadující viditelnost. Hodnota obsahuje jenom informativní řetězec. Hodnota je obvykle `reg_dword` nastavena na hodnotu 0.|  

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
 [Balíčky VSPackage](../extensibility/internals/vspackages.md)