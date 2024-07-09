import {
    baseURL,
    testCase,
    visitWithCookie,
} from '../../../../support/utils/commands';
import { city } from '../../../../support/utils/selectors';
import { productListingCategoryLinks } from '../../../../support/productListing/links';
import { productListing } from '../../../../support/productListing/selectors';
import { addProductToFavorite } from '../../../../support/favorite/commands';
import { favorite, favoriteHeader } from '../../../../support/favorite/selectors';
import { header } from '../../../../support/mainPage/selectors';

describe('chayka-1 - Избранное, листинг', () => {
    testCase(() => {
        it('Добавление одежды в избранное с листинга', () => {
            visitWithCookie(baseURL() + productListingCategoryLinks.tekstilOdezhda, city.Moscow);
            cy.get(productListing.item).first().realHover();
            addProductToFavorite(productListing.addToFavorite, 0, 1);
            cy.get(header.favoritePage).clickAndWait();
            cy.get(favorite.header).should('have.text', 'Избранное');
            cy.get('.card_imgVertical__xoxhu').each(($img) => {
                const height = $img.height();
                const width = $img.width();
                expect(height).to.be.greaterThan(width); // Проверка на вертикальную ориентацию
            });
        });
    });
});
