---
title: Registrace vyhodnocovače výrazů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluators, registering
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 29aaef797ad18fd63e4f587901dbf3b29dbb73b0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51808328"
---
# <a name="registering-an-expression-evaluator"></a>Registrace vyhodnocovače výrazů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  V sadě Visual Studio 2015 je zastaralý tímto způsobem implementace vyhodnocovače výrazů. Informace o implementace vyhodnocovače výrazů modulu CLR najdete v tématu [vyhodnocovače výrazů modulu CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [spravované ukázka Chyba při vyhodnocování výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Chyba při vyhodnocování výrazu (EE) musí registrovat jako objekt pro vytváření tříd pomocí prostředí Windows COM i Visual Studio. EE je implementován jako knihovna DLL tak, že mohou být vloženy do adresního prostoru ladicí stroj (DE) nebo Visual Studio adresní prostor, v závislosti na tom, který vytvoří instanci entity EE.  
  
## <a name="managed-code-expression-evaluator"></a>Chyba při vyhodnocování výrazu spravovaný kód  
 Spravovaný kód EE je implementován jako knihovna tříd, což je knihovnu DLL, která se zaregistruje ve službě prostředí modelu COM, obvykle spuštěna voláním do programu VSIP **regpkg.exe**. Skutečný proces vytváření klíčů registru pro prostředí modelu COM je automaticky zpracována.  
  
 Metoda hlavní třídy je označena <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>, označující, že je metoda se volá, když se knihovna DLL je registrována pomocí modelu COM. Tento způsob registrace, často označované jako `RegisterClass`, provede úlohu registrace knihovny DLL pomocí sady Visual Studio. Odpovídající `UnregisterClass` (označené <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>), následky `RegisterClass` při odinstalaci knihovny DLL.  
  
 Jako u EE napsanou v nespravovaném kódu; jsou vytvořeny stejným položky registru jediným rozdílem je, že nemá žádné pomocná funkce, jako `SetEEMetric` proveďte práci za vás. Příklad tohoto procesu registrace nebo zrušení registrace vypadá takto:  
  
### <a name="example"></a>Příklad  
 Tato funkce ukazuje, jak spravovaný kód EE zaregistruje a samotné zruší registraci pomocí sady Visual Studio.  
  
```csharp  
namespace EEMC  
{  
    [GuidAttribute("462D4A3D-B257-4AEE-97CD-5918C7531757")]  
    public class EEMCClass : IDebugExpressionEvaluator  
    {  
        #region Register and unregister.  
        private static Guid guidMycLang = new Guid("462D4A3E-B257-4AEE-97CD-5918C7531757");  
        private static string languageName = "MyC";  
        private static string eeName = "MyC Expression Evaluator";  
  
        private static Guid guidMicrosoftVendor = new Guid("994B45C4-E6E9-11D2-903F-00C04FA302A1");  
        private static Guid guidCOMPlusOnlyEng = new Guid("449EC4CC-30D2-4032-9256-EE18EB41B62B");  
        private static Guid guidCOMPlusNativeEng = new Guid("92EF0900-2251-11D2-B72E-0000F87572EF");  
  
        /// <summary>  
        /// Register the expression evaluator.  
        /// Set "project properties/configuration properties/build/register for COM interop" to true.  
        /// </summary>  
         [ComRegisterFunctionAttribute]  
        public static void RegisterClass(Type t)  
        {  
            // Get Visual Studio version (set by regpkg.exe)  
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");  
            string s = @"SOFTWARE\Microsoft\VisualStudio\"  
                        + hive  
                        + @"\AD7Metrics\ExpressionEvaluator";  
  
            RegistryKey rk = Registry.LocalMachine.CreateSubKey(s);  
            if (rk == null)  return;  
  
            rk = rk.CreateSubKey(guidMycLang.ToString("B"));  
            rk = rk.CreateSubKey(guidMicrosoftVendor.ToString("B"));  
            rk.SetValue("CLSID", t.GUID.ToString("B"));  
            rk.SetValue("Language", languageName);  
            rk.SetValue("Name", eeName);  
  
            rk = rk.CreateSubKey("Engine");  
            rk.SetValue("0", guidCOMPlusOnlyEng.ToString("B"));  
            rk.SetValue("1", guidCOMPlusNativeEng.ToString("B"));  
        }  
        /// <summary>  
        /// Unregister the expression evaluator.  
        /// </summary>  
         [ComUnregisterFunctionAttribute]  
        public static void UnregisterClass(Type t)  
        {  
            // Get Visual Studio version (set by regpkg.exe)  
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");  
            string s = @"SOFTWARE\Microsoft\VisualStudio\"  
                        + hive  
                        + @"\AD7Metrics\ExpressionEvaluator\"  
                        + guidMycLang.ToString("B");  
            RegistryKey key = Registry.LocalMachine.OpenSubKey(s);  
            if (key != null)  
            {  
                key.Close();  
                Registry.LocalMachine.DeleteSubKeyTree(s);  
            }  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code-expression-evaluator"></a>Chyba při vyhodnocování výrazu nespravovaného kódu  
 EE knihovna DLL opakovaně implementuje `DllRegisterServer` funkce k registraci v prostředí modelu COM, stejně jako Visual Studio.  
  
> [!NOTE]
>  Kód MyCEE ukázkový kód registru najdete v souboru dllentry.cpp, který je umístěn v programu VSIP instalace v části EnVSDK\MyCPkgs\MyCEE.  
  
### <a name="dll-server-process"></a>Proces serveru knihovny DLL  
 Při registraci EE, server knihovny DLL:  
  
1.  Zaregistruje jeho objekt pro vytváření tříd `CLSID` podle konvence normální COM.  
  
2.  Zavolá pomocnou funkci `SetEEMetric` k registraci ve službě Visual Studio EE metrik zobrazených v následující tabulce. Funkce `SetEEMetric` a metriky níže uvedených jsou součástí knihovny dbgmetric.lib. Zobrazit [Pomocníci sad SDK pro ladění](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) podrobnosti.  
  
    |Metrika|Popis|  
    |------------|-----------------|  
    |`metricCLSID`|`CLSID` Třída továrny EE|  
    |`metricName`|Název EE jako řetězec annotable|  
    |`metricLanguage`|Název jazyka, který je EE určená k vyhodnocení|  
    |`metricEngine`|`GUID`s ladicími stroji (DE), které využívají tento EE|  
  
    > [!NOTE]
    >  `metricLanguage``GUID` Určuje jazyk podle názvu, ale je `guidLang` argument `SetEEMetric` , který vybere jazyk. Když kompilátor generuje soubor s informacemi o ladění, by měl napsat odpovídající `guidLang` tak, aby DE ví, které EE určený. Poskytovatel symbolů DE obvykle vyzve k zadání tohoto jazyka `GUID`, který je uložen v souboru ladicí informace.  
  
3.  Zaregistruje pomocí sady Visual Studio tak, že vytvoříte klíče HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*X.Y*, kde *X.Y* je verze sady Visual Studio k registraci ve službě.  
  
### <a name="example"></a>Příklad  
 Tato funkce ukazuje, jak nespravovaný kód (C++) EE zaregistruje a samotné zruší registraci pomocí sady Visual Studio.  
  
```cpp#  
/*---------------------------------------------------------  
  Registration  
-----------------------------------------------------------*/  
#ifndef LREGKEY_VISUALSTUDIOROOT  
    #define LREGKEY_VISUALSTUDIOROOT L"Software\\Microsoft\\VisualStudio\\8.0"  
#endif  
  
static HRESULT RegisterMetric( bool registerIt )  
{  
    // check where we should register  
    const ULONG cchBuffer = _MAX_PATH;  
    WCHAR wszRegistrationRoot[cchBuffer];  
    DWORD cchFreeBuffer = cchBuffer - 1;  
    wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT_NOVERSION);  
    wcscat(wszRegistrationRoot, L"\\");  
  
    // this is Environment SDK specific  
    // we check for  EnvSdk_RegKey environment variable to  
    // determine where to register  
    DWORD cchDefRegRoot = lstrlenW(LREGKEY_VISUALSTUDIOROOT_NOVERSION) + 1;  
    cchFreeBuffer = cchFreeBuffer - cchDefRegRoot;  
    DWORD cchEnvVarRead = GetEnvironmentVariableW(  
        /* LPCTSTR */ L"EnvSdk_RegKey", // environment variable name  
        /* LPTSTR  */ &wszRegistrationRoot[cchDefRegRoot],// buffer for variable value  
        /* DWORD   */ cchFreeBuffer);// size of buffer  
    if (cchEnvVarRead >= cchFreeBuffer)  
        return E_UNEXPECTED;  
    // If the environment variable does not exist then we must use   
    // LREGKEY_VISUALSTUDIOROOT which has the version number.  
    if (0 == cchEnvVarRead)  
        wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT);  
  
    if (registerIt)  
    {  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricCLSID,  
                    CLSID_MycEE,  
                    wszRegistrationRoot );  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricName,  
                    GetString(IDS_INFO_MYCDESCRIPTION),  
                    wszRegistrationRoot );  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricLanguage, L"MyC",  
                    wszRegistrationRoot);  
  
        GUID engineGuids[2];  
        engineGuids[0] = guidCOMPlusOnlyEng;  
        engineGuids[1] = guidCOMPlusNativeEng;  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricEngine,  
                    engineGuids,  
                    2,  
                    wszRegistrationRoot);  
    }  
    else  
    {  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricCLSID,  
                        wszRegistrationRoot);  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricName,  
                        wszRegistrationRoot );  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricLanguage,  
                        wszRegistrationRoot );  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricEngine,  
                        wszRegistrationRoot );  
    }  
  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Zápis vyhodnocovací filtr výrazů modulu CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Pomocníci sad SDK pro ladění](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)

