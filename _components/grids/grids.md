---
title: Grid Styles
scss: '_sass/components/m-grid.scss'
type: grids
exclude_from_search: true
---

<div class="mi-grid subscriptions" ng-show="packs.length > 0">
    <div class="mi-grid-table">
      <div class="mi-grid-body">
        <table class="tbl-fixed mi-grid-responsive">
          <col ng-class="{'first-col': $state.includes('subscriptionAdd')}">
          <col class="mobile-hidden" ng-class="{'second-col': $state.includes('subscriptionAdd')}">
          <col ng-class="{'third-col': $state.includes('subscriptionAdd')}">
          <tr class="mi-grid-th-row">
            <th class="subscription-table-header mi-grid-column Grid1Col1 grid-cell-left head-1 ui-btn-up-b">Pack</th>
            <th ng-if="!$state.includes('subscriptionAdd')" class="subscription-table-header mi-grid-column Grid1Col2 mobile-hidden grid-cell-left head-2 ui-btn-up-b">Users</th>
            <th class="subscription-table-header mi-grid-column Grid1Col3 mobile-hidden grid-cell-center head-3 sub-user-num ui-btn-up-b"># of Users</th>
            <th ng-if="!$state.includes('subscriptionAdd')" class="subscription-table-header mi-grid-column Grid1Col4 mobile-hidden grid-cell-center head-4 ui-btn-up-b">Per User</th>
            <th class="subscription-table-header mi-grid-column Grid1Col5 grid-cell-center head-5 ui-btn-up-b">Total Cost</th>
          </tr>
         
          <tr ng-if="!$state.includes('subscriptionAdd')" class="mi-grid-row-click" ui-sref="subscriptionManagePacks({ packId: pack.id })" data-ng-show="pack.isInstalled" data-ng-repeat="pack in packs">
          
            <td class="grid-cell-left">
              <span>
                {{pack.name}}
              </span>
              <div ng-if="$state.includes('subscriptionAdd')">
                
                  <mi-context-menu menu-icon="'mi-icon-info-sign'" open-on-hover="true">
                      <menu-options>
                          <ul>
                              <label for="">Contains</label>
                              <li data-ng-repeat="pack in pack.apps">
                                  {{pack.name}}
                              </li>
                          </ul>
                      </menu-options>
                  </mi-context-menu>
                
              </div>
            </td>
            
            <td ng-if="!$state.includes('subscriptionAdd')" title="{{ pack.usernames }}" class="grid-cell-left mi-grid-no-break mobile-hidden">
              <span>
                {{ pack.usernames }}
              </span>
            </td>
            <td class="grid-cell-center mobile-hidden">
              {{ pack.userIds.length }}
            </td>
           <td ng-if="!$state.includes('subscriptionAdd')" class="grid-cell-center mobile-hidden">
              {{ pack.type == 'Private' ? 'FREE' : (pack.price | currency:"$":0) }}
            </td>
            <td class="grid-cell-center lastvisible-desktop lastvisible-mobile">
              {{ pack.type == 'Private' ? 'FREE' : (pack.cost | currency:"$":0) }}
            </td>
          </tr>          

          <tr ng-if="$state.includes('subscriptionAdd')" class="noclick" data-ng-show="pack.isInstalled" data-ng-repeat="pack in packs">
          
            <td class="grid-cell-left">
              <span>
                {{pack.name}}
              </span>
              <div ng-if="$state.includes('subscriptionAdd')">
                
                  <mi-context-menu menu-icon="'mi-icon-info-sign'" open-on-hover="true">
                      <menu-options>
                          <ul>
                              <label for="">Contains</label>
                              <li data-ng-repeat="pack in pack.apps">
                                  {{pack.name}}
                              </li>
                          </ul>
                      </menu-options>
                  </mi-context-menu>
                
              </div>
            </td>
            
            <td ng-if="!$state.includes('subscriptionAdd')" title="{{ pack.usernames }}" class="grid-cell-left mi-grid-no-break mobile-hidden">
              <span>
                {{ pack.usernames }}
              </span>
            </td>
            <td class="grid-cell-center mobile-hidden">
              {{ pack.userIds.length }}
            </td>
           <td ng-if="!$state.includes('subscriptionAdd')" class="grid-cell-center mobile-hidden">
              {{ pack.type == 'Private' ? 'FREE' : (pack.price | currency:"$":0) }}
            </td>
            <td class="grid-cell-center lastvisible-desktop lastvisible-mobile">
              {{ pack.type == 'Private' ? 'FREE' : (pack.cost | currency:"$":0) }}
            </td>
          </tr>          
        </table>
      </div>
    </div>
  </div>
  <a ng-if="$state.includes('subscriptionAdd')" class="modify-link" ng-click="subscribeModify()" ui-sref="subscription" >Manage</a>

  <!-- Subscription grid END ^^ -->