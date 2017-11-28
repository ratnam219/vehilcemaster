<%@ Page Language="C#" AutoEventWireup="true" CodeFile="frmVehicleMaster.aspx.cs"
    Inherits="frmVehicleMaster" %>

<%@ Register Src="~/dlhEmist/SearchTextBox/SearchTextBox.ascx" TagName="SearhTextBox"
    TagPrefix="uc1" %>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
    <title>Vehicle Master</title>
    <link href="~/dlhEmist/App_Themes/eFleet.css" runat="server" id="Link1" rel="stylesheet"
        type="text/css" />
    <link href="../../../../App_Themes/jthemes/efleet/jquery-ui.min.css" rel="stylesheet"
        type="text/css" />
    <script src="../../../../Scripts/polyfill.min.js" type="text/javascript"></script>
    <script src="../../../../Scripts/jquery-min-1.11.2.js" type="text/javascript"></script>
    <script src="../../../SearchTextBox/SearchTextBox.js" type="text/javascript"></script>
    <script src="../../../Common/_Common.js" type="text/javascript"></script>
    <script src="../../../../AjaxForm/Script/UserValidation.js" type="text/javascript"></script>
    <script src="../../../Common/dateConverter.js" type="text/javascript"></script>
    <script src="../../../Common/DateValidation.js" type="text/javascript"></script>
    <script src="../../../Common/DateValidator.js" type="text/javascript"></script>
    <script src="../../../Common/CommonJS.js" type="text/javascript"></script>
    <script src="../../../../Scripts/jPopup.min.js" type="text/javascript"></script>
    <script src="Scripts/frmVehicleMaster_Js.js" type="text/javascript"></script>
</head>
<body onload="VehicleInt();">
    <form id="form1" runat="server">
    <div>
        <table class="lblHeading">
            <tr class="subheadingNew">
                <td colspan="20" id="lblInstanceID" class="FormCaption" valign="top">
                    Vehicle Master
                </td>
            </tr>
            <tr><td colspan="20"><hr /></td></tr>
            <tr>
                <td>
                    <table>
                        <tr>
                            <td>
                                <table>
                                    <tr>
                                        <td id="lblVehicleSearch" class="subheading">
                                            Vehicle
                                        </td>
                                        <td>
                                            :
                                        </td>
                                        <td>
                                            <uc1:SearhTextBox ID="txtVehicleSTB" runat="server" CssClass="Searchtextclass" />
                                        </td>
                                    </tr>
                                </table>
                            </td>
                            <td>
                            </td>
                            <td>
                                <table align="right">
                                    <tr>
                                        <td>
                                            <select id="cmbtrashFIL" runat="server" class="lblHeading">
                                                <option value="0">-- Select --</option>
                                                <option value="3">Trash</option>
                                            </select>
                                            <input id="cmdShow" class="XPButton" type="button" value="ShowAll" onclick="Show('VehicleNo');" />
                                            <input id="cmdReset" class="XPButton" type="button" value="Reset" onclick="Reset();" />
                                            <input id="cmdExport" type="button" runat="server" class="XPButton" value="Export"
                                                onserverclick="cmdExport_Click" tabindex = "-1" usesubmitbehavior="false"/>
                                        </td>
                                    </tr>
                                </table>
                            </td>
                        </tr>
                    </table>
                </td>
            </tr>
            <tr>
                <td class="subheadingNew" colspan="20">
                    Vehicle Details
                </td>
            </tr>
            <tr>
                <td colspan="20">
                    <table>
                        <tr>
                            <td>
                                <table>
                                    <tr>
                                        <td valign="top">
                                            <table>
                                                <tr>
                                                    <td id="tdVehicleCode" valign="top" class="subheading">
                                                        Vehicle Code
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top">
                                                        <input type="text" id="txtVehicleNo" runat="server" class="Searchtextclass" />
                                                    </td>
                                                </tr>
                                                <tr>
                                                    <td valign="top" id="tdManufacturingYear" class="subheading">
                                                        Manufacturing Year
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top" class="subheading">
                                                        <input type="text" id="txtMenufacturerYear" class="Searchtextclass" runat="server"
                                                            maxlength="4" style="width: 110px" onblur="numberOnly(this);" onchange="CheckDateVehicleManufactureyear();" />
                                                        [YYYY]
                                                    </td>
                                                </tr>
                                                <tr>
                                                    <td valign="top" id="tdOfficeSearch" class="subheading">
                                                        Office
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top">
                                                        <uc1:SearhTextBox ID="txtOfficeSTB" runat="server" CssClass="Searchtextclass" />
                                                    </td>
                                                </tr>
                                                <tr>
                                                    <td class="subheading" id="tdVehicleOwnerParty" valign="top">
                                                        Vehicle Owner Party
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top">
                                                        <uc1:SearhTextBox ID="txtOwnerPartySTB" runat="server" CssClass="Searchtextclass" />
                                                    </td>
                                                </tr>
                                                <tr>
                                                    <td class="subheading" valign="top" id="tdModel">
                                                        Model
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top">
                                                        <uc1:SearhTextBox ID="txtModelSTB" runat="server" CssClass="Searchtextclass" />
                                                    </td>
                                                </tr>
                                                <tr>
                                                    <td class="subheading" valign="top" id="tdLoadCapacity">
                                                        Load Capacity
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td>
                                                        <uc1:SearhTextBox ID="txtLoadCapacitySTB" runat="server" CssClass="Searchtextclass" />
                                                    </td>
                                                </tr>
                                                <tr>
                                                    <td valign="top" class="subheading" id="tdRegistrationNo">
                                                        Registration No
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top">
                                                        <input type="text" id="txtRegistrationNO" runat="server" class="Searchtextclass" />
                                                    </td>
                                                </tr>
                                                <tr>
                                                    <td valign="top" class="subheading" id="tdRegistrationDate">
                                                        Registration Date
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top">
                                                        <input type="text" id="txtRegistrationDate" class="Searchtextclass" runat="server"
                                                            onblur="PopulateChangedDate(this,false);" />
                                                    </td>
                                                </tr>
                                                <tr>
                                                    <td valign="top" class="subheading" id="tdPurchaseDate">
                                                        Purchase Date
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top">
                                                        <input type="text" id="txtPurchaseDate" runat="server" class="Searchtextclass" onblur="PopulateChangedDate(this,false);" />
                                                    </td>
                                                </tr>
                                                <tr>
                                                    <td valign="top" class="subheading" id="tdPurchaseAmount">
                                                        Purchase Amount
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top">
                                                        <input type="text" id="txtPurchaseAmount" runat="server" class="Searchtextclass"
                                                            onblur="numberOnly(this);" />
                                                    </td>
                                                </tr>
                                                <tr>
                                                    <td valign="top" id="tdSoldDate" class="subheading">
                                                        Sold Date
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top">
                                                        <input type="text" id="txtSoldDate" class="Searchtextclass" runat="server" onblur="PopulateChangedDate(this,false);" />
                                                    </td>
                                                </tr>
                                                <tr>
                                                    <td valign="top" class="subheading" id="tdSaleAmount">
                                                        Sale Amount
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top">
                                                        <input type="text" id="txtSaleAmount" runat="server" class="Searchtextclass" onblur="numberOnly(this);" />
                                                    </td>
                                                </tr>
                                                 <tr class="subheading"><td id="tdCustom1">Custom1</td><td>:</td><td><input type="text" id="txtCustom1" runat="server" class="Searchtextclass"/></td></tr>
                                                    <tr class="subheading"><td id="tdCustom2">Custom2</td><td>:</td><td><input type="text" id="txtCustom2" runat="server" class="Searchtextclass"/></td></tr>
                                                    <tr class="subheading"><td id="tdCustom3">Custom3</td><td>:</td><td><input type="text" id="txtCustom3" runat="server" class="Searchtextclass"/></td></tr>
                                                    <tr class="subheading"><td id="tdCustom4">Custom4</td><td>:</td><td><input type="text" id="txtCustom4" runat="server" class="Searchtextclass"/></td></tr>
                                                    <tr class="subheading"><td id="tdCustom5">Custom5</td><td>:</td><td><input type="text" id="txtCustom5" runat="server" class="Searchtextclass"/></td></tr>
                                                     <tr class="subheading"><td id="tdCustom6">Custom6</td><td>:</td><td><input type="text" id="txtCustom6" runat="server" class="Searchtextclass"/></td></tr>
                                                      <tr class="subheading"><td id="tdCustom7">Custom7</td><td>:</td><td><input type="text" id="txtCustom7" runat="server" class="Searchtextclass"/></td></tr>
                                                       <tr class="subheading"><td id="tdCustom8">Custom8</td><td>:</td><td><input type="text" id="txtCustom8" runat="server" class="Searchtextclass"/></td></tr>
                                            </table>
                                        </td>
                                        <td valign="top">
                                            <table>
                                                <tr>
                                                    <td valign="top" class="subheading" id="tdChassisNo">
                                                        Chassis No
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top">
                                                        <input type="text" id="txtChessisNo" runat="server" maxlength="30" class="Searchtextclass" />
                                                    </td>
                                                </tr>
                                                <tr>
                                                    <td valign="top" class="subheading" id="tdEngineNo">
                                                        Engine No
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top">
                                                        <input type="text" id="txtEngineNo" class="Searchtextclass" maxlength="30" runat="server" />
                                                    </td>
                                                </tr>
                                                <tr>
                                                    <td valign="top" class="subheading" id="tdTrollyChassisNo">
                                                        Trolly Chassis No
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top">
                                                        <input type="text" id="txtTrollyChessisNo" class="Searchtextclass" runat="server" />
                                                    </td>
                                                </tr>
                                                <tr>
                                                    <td valign="top" id="tdGrossVehicleWeight" class="subheading">
                                                        Gross Vehicle Weight
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top">
                                                        <input type="text" id="txtGrossVehicleWeight" class="Searchtextclass" runat="server"
                                                            onblur="numberOnly(this);" />
                                                    </td>
                                                </tr>
                                                <tr>
                                                    <td class="subheading" valign="top" id="tdUnLadenWeight">
                                                        UnLaden Weight
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top">
                                                        <input type="text" id="txtUnLadenWeight" runat="server" class="Searchtextclass" onblur="numberOnly(this);" />
                                                    </td>
                                                </tr>
                                                <tr>
                                                    <td class="subheading" id="tdDriverSalary" valign="top">
                                                        Driver Salary
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top">
                                                        <input type="text" id="txtDriverSalary" runat="server" class="Searchtextclass" onblur="numberOnly(this);" />
                                                    </td>
                                                </tr>
                                                <tr>
                                                    <td valign="top" id="tdVehicleTypeSearch" class="subheading">
                                                        Vehicle Type
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top">
                                                        <uc1:SearhTextBox ID="txtSearchVehicleTypeSTB" runat="server" CssClass="Searchtextclass" />
                                                    </td>
                                                </tr>
                                                <tr>
                                                    <td valign="top" class="subheading" id="tdInstallment">
                                                        Installment
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top">
                                                        <input type="text" id="txtInstallment" class="Searchtextclass" runat="server" onblur="numberOnly(this);" />
                                                    </td>
                                                </tr>
                                                <tr>
                                                    <td valign="top" class="subheading" id="tdDueAmount">
                                                        Due Amount
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top">
                                                        <input type="text" id="txtDueAmount" runat="server" class="Searchtextclass" onblur="numberOnly(this);" />
                                                    </td>
                                                </tr>
                                                <tr>
                                                    <td valign="top" class="subheading" id="tdGeneralExpense">
                                                        General Expense
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top">
                                                        <input type="text" id="txtGeneralExpense" class="Searchtextclass" runat="server"
                                                            onblur="numberOnly(this);" />
                                                    </td>
                                                </tr>
                                                <tr>
                                                    <td class="subheading">
                                                        Block For
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top">
                                                        <select id="cmbBlockVehicleFor" runat="server" class="lblHeading">
                                                        </select>
                                                    </td>
                                                </tr>
                                                <tr>
                                                    <td class="subheading">
                                                        Attached Vehicle
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top">
                                                        <input type="checkbox" id="chkAttached" runat="server" />
                                                    </td>
                                                </tr><tr>
                                                    <td class="subheading">
                                                        Bypass Fuel Avg Bdgt in Route
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top">
                                                        <input type="checkbox" id="chkPassBudgtRoute" runat="server" />
                                                    </td>
                                                </tr>
                                                <tr>
                                                    <td valign="top" class="subheading" id="td1">
                                                        Division
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top">
                                                         <uc1:SearhTextBox ID="txtDivision" runat="server" CssClass="Searchtextclass" />
                                                    </td>
                                                </tr>
                                            </table>
                                        </td>
                                        <td valign="top">
                                            <table>
                                                <tr>
                                                    <td valign="top" id="tdACFuelCons" class="subheading">
                                                        AC Fuel Consumption
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top">
                                                        <input type="text" id="txtACFuelConsumption" runat="server" class="Searchtextclass"
                                                            onblur="numberOnly(this);" />
                                                    </td>
                                                </tr>
                                                <tr>
                                                    <td valign="top" id="tdCost" class="subheading">
                                                        Cost / KM
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top">
                                                        <input type="text" id="txtCostPerKM" runat="server" class="Searchtextclass" onblur="numberOnly(this);" />
                                                    </td>
                                                </tr>
                                                <tr>
                                                    <td valign="top" id="tdRevenue" class="subheading">
                                                        Revenue / KM
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top">
                                                        <input type="text" id="txtRevenuePerKM" runat="server" class="Searchtextclass" onblur="numberOnly(this);" />
                                                    </td>
                                                </tr>
                                                <tr>
                                                    <td valign="top" id="tdFavg" class="subheading">
                                                        Fuel Avg
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top">
                                                        <input type="text" id="txtAverage" runat="server" class="Searchtextclass" onblur="numberOnly(this);" />
                                                    </td>
                                                </tr>
                                                <tr>
                                                    <td valign="top" id="tdFuelAvgEmpty" class="subheading">
                                                        Fuel Avg Empty
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top">
                                                        <input type="text" id="txtFuelAvgEmpty" class="Searchtextclass" runat="server" onblur="numberOnly(this);" />
                                                    </td>
                                                </tr>
                                                <tr>
                                                    <td valign="top" id="tdFuelAvgLocal" class="subheading">
                                                        Fuel Avg Local
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top">
                                                        <input type="text" id="txtLocal" runat="server" class="Searchtextclass" />
                                                    </td>
                                                </tr>
                                                <tr>
                                                    <td valign="top" id="tdFuelAvgHighway" class="subheading">
                                                        Fuel Avg Highway
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top">
                                                        <input type="text" id="txtHighway" class="Searchtextclass" runat="server" onblur="numberOnly(this);" />
                                                    </td>
                                                </tr>
                                                <tr>
                                                    <td valign="top" id="tdFuelAvgCustom" class="subheading">
                                                        Fuel Avg Custom
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top">
                                                        <input type="text" id="txtcustom" runat="server" class="Searchtextclass" onblur="numberOnly(this);" />
                                                    </td>
                                                </tr>
                                                <tr>
                                                    <td valign="top" id="tdAlias1" class="subheading">
                                                        Alias 1
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top">
                                                        <input type="text" id="txtAlias1" class="Searchtextclass" runat="server" />
                                                    </td>
                                                </tr>
                                                <tr>
                                                    <td valign="top" class="subheading" id="tdAlias2">
                                                        Alias 2
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top">
                                                        <input type="text" id="txtAlias2" runat="server" class="Searchtextclass" />
                                                    </td>
                                                </tr>
                                                <tr>
                                                    <td valign="top" class="subheading" id="tdAlias3">
                                                        Alias 3
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top">
                                                        <input type="text" id="txtAlias3" runat="server" class="Searchtextclass" />
                                                    </td>
                                                </tr>
                                                <tr>
                                                    <td valign="top" class="subheading" id="tdNature">
                                                        Default Route Nature
                                                    </td>
                                                    <td>
                                                        :
                                                    </td>
                                                    <td valign="top">
                                                        <select id="cmbNature" runat="server" class="lblHeading">
                                                            <option selected="selected" value="0">---Select---</option>
                                                        </select>
                                                    </td>
                                                </tr>
                                            </table>
                                        </td>
                                    </tr>
                                </table>
                            </td>
                        </tr>
                    </table>
                </td>
            </tr>
            <tr>
                <td colspan="20" class="subheadingNew">
                    <table style="width: 100%">
                        <tr>
                            <td colspan="5" class="FormSectionLinks">
                                <a id="A2" href="javascript:void(0);" onclick="OpenCard();" class="link">Fleet Card</a> <a id="hlAttachPhoto"
                                    href="javascript:void(0);" onclick="AttachPhoto();" class="link">Attach Photo</a> <a href="javascript:void(0);" class="link"
                                        onclick="getHelpPopup();">Help</a> <a id="hlUserSessionInfo" class="link" href="javascript:void(0);"
                                            onclick="UserInfo();">Session Info</a> <a id="A1" class="link" href="javascript:void(0);" onclick="ShowMasterAlias();">
                                                Master Alias</a> <a id="A3" class="link" href="javascript:void(0);" onclick="ShowVehicleDueMapping();">
                                                    Dues</a> <a id="A4" class="link" href="javascript:void(0);" onclick="ShowAccountCategory();">Category/Class</a>
                                <a id="A5" class="link" href="javascript:void(0);" onclick="ShowVehicleBudgeting();">Vehicle Budgeting</a>
                                <a id="A6" class="link" href="javascript:void(0);" onclick="AttachFuelDetails();">Fuel Budgeting</a>
                                <a id="A7" class="link" href="javascript:void(0);" onclick="AttachSellPurchase();">Sell/Purchase</a>
                            </td>
                            <td align="right">
                                <input id="cmdSave" class="XPButton" type="button" value="Save" onclick="SaveUpdateVechileModel();" />
                            </td>
                        </tr>
                    </table>
                </td>
            </tr>
            <tr class="subheadingNew">
                <td colspan="20">
                    Vehicle Details
                </td>
            </tr>
            <tr>
                <td>
                    <table>
                        <tr>
                            <td colspan="2">
                                <input type="text" id="txtPageNo" onblur="Show('VehicleNo')" class="AMTTextBox" />
                                Of <span id="lblTotalPage" class="subheading" />
                            </td>
                            <td colspan="2">
                                PageSize
                                <input type="text" id="txtPageSize" maxlength="3" class="AMTTextBox" />
                            </td>
                        </tr>
                    </table>
                </td>
            </tr>
            <tr>
                <td colspan="3">
                    <table>
                        <tr>
                            <td>
                                <table id="tdVehiclesDetails">
                                    <thead>
                                        <tr id="tHeader">
                                            <th id="VehicleNo" class="HeaderStyle">
                                                Vehicle Code
                                            </th>
                                            <th id="Office" class="HeaderStyle">
                                                Office
                                            </th>
                                            <th id="RegistrationNo" class="HeaderStyle">
                                                Registration No
                                            </th>
                                            <th id="ManufacturingYear" class="HeaderStyle">
                                                Year
                                            </th>
                                            <th id="Party" class="HeaderStyle">
                                                Party
                                            </th>
                                            <th id="Model" class="HeaderStyle">
                                                Model
                                            </th>
                                            <th id="ChassisNo" class="HeaderStyle">
                                                Chassis No
                                            </th>
                                            <th id="EngineNo" class="HeaderStyle">
                                                Engine No
                                            </th>
                                            <th id="VehicleType" class="HeaderStyle">
                                                Vehicle Type
                                            </th>
                                            <th id="Action" class="HeaderStyle">
                                                Action
                                            </th>
                                        </tr>
                                    </thead>
                                    <tbody id="tDetail">
                                    </tbody>
                                </table>
                            </td>
                        </tr>
                    </table>
                </td>
            </tr>
        </table>
    </div>
    </form>
</body>
</html>
