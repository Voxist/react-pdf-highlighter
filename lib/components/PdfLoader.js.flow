// @flow

import React, { Component } from "react";

import type { T_PDFJS, T_PDFJS_Document } from "../types";

import pdfjs from "pdfjs-dist/webpack";

type Props = {
  url: string,
  beforeLoad: React$Element<*>,
  children: (pdfDocument: T_PDFJS_Document) => React$Element<*>,
  setPdfDoc?: (pdfDocument: T_PDFJS_Document) => void
};

type State = {
  pdfDocument: ?T_PDFJS_Document
};

class PdfLoader extends Component<Props, State> {
  state = {
    pdfDocument: null
  };

  componentDidMount() {
    const { url, setPdfDoc } = this.props;

    pdfjs.getDocument(url).promise.then(pdfDocument => {
      if (setPdfDoc) {
        setPdfDoc(pdfDocument);
      }
      this.setState({
        pdfDocument: pdfDocument
      });
    });
  }

  render() {
    const { children, beforeLoad } = this.props;
    const { pdfDocument } = this.state;

    if (pdfDocument) {
      return children(pdfDocument);
    }

    return beforeLoad;
  }
}

export default PdfLoader;
